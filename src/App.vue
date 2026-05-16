<script setup>
// Importamos o método reactive do Vue, que permite criar um objeto reativo.
// Objetos reativos são observados pelo Vue, e qualquer alteração neles reflete automaticamente na interface.
import { reactive } from "vue";

// Importamos os três componentes que compõem nossa aplicação:
// - Cabecalho: mostra o título e a quantidade de tarefas pendentes.
// - Formulario: permite cadastrar novas tarefas e escolher o filtro.
// - ListaDeTarefas: exibe as tarefas filtradas e permite marcar como concluídas ou excluir.
import Cabecalho from "./components/Cabecalho.vue";
import Formulario from "./components/Formulario.vue";
import ListaDeTarefas from "./components/ListaDeTarefas.vue";

// Criamos o estado global da aplicação usando reactive.
// Esse objeto "estado" contém:
// - filtro: indica qual filtro está ativo (todas, pendentes ou finalizadas).
// - tarefaTemp: armazena temporariamente o texto digitado no formulário.
// - tarefas: é a lista de tarefas cadastradas (inicialmente vazia).
const estado = reactive({
  filtro: "todas",
  tarefaTemp: "",
  tarefas: [],
});

// Função que retorna apenas as tarefas pendentes (finalizada = false).
const getTarefasPendentes = () => {
  return estado.tarefas.filter((tarefa) => !tarefa.finalizada);
};

// Função que retorna apenas as tarefas finalizadas (finalizada = true).
const getTarefasFinalizadas = () => {
  return estado.tarefas.filter((tarefa) => tarefa.finalizada);
};

// Função que retorna as tarefas filtradas de acordo com o estado.filtro.
// Se o filtro for "pendentes", retorna apenas pendentes.
// Se for "finalizadas", retorna apenas finalizadas.
// Caso contrário (default), retorna todas.
const getTarefasfiltradas = () => {
  const { filtro } = estado;

  switch (filtro) {
    case "pendentes":
      return getTarefasPendentes();
    case "finalizadas":
      return getTarefasFinalizadas();
    default:
      return estado.tarefas;
  }
};

// Função responsável por cadastrar uma nova tarefa.
// Ela cria um objeto tarefaNova com título vindo de tarefaTemp e finalizada = false.
// Depois adiciona essa tarefa na lista e limpa o campo tarefaTemp.
const cadastraTarefa = () => {
  const tarefaNova = {
    titulo: estado.tarefaTemp,
    finalizada: false,
  };

  estado.tarefas.push(tarefaNova);
  estado.tarefaTemp = "";
};

// Função responsável por deletar uma tarefa.
// Recebe a tarefa como parâmetro e filtra a lista removendo essa tarefa.
const deletarTarefa = (tarefa) => {
  estado.tarefas = estado.tarefas.filter((t) => t !== tarefa);
};
</script>

<template>
  <!-- Container principal que segura todos os componentes -->
  <div class="container">
    <!-- Componente Cabecalho recebe como prop a quantidade de tarefas pendentes -->
    <Cabecalho :tarefas-pendentes="getTarefasPendentes().length" />

    <!-- Componente Formulario recebe várias props:
         - trocar-filtro: função que altera o filtro no estado
         - tarefa-temp: valor atual digitado no input
         - edita-tarefa-temp: função que atualiza tarefaTemp conforme o usuário digita
         - cadastra-taterefa: função que cadastra uma nova tarefa -->
    <Formulario
      :trocar-filtro="(evento) => (estado.filtro = evento.target.value)"
      :tarefa-temp="estado.tarefaTemp"
      :edita-tarefa-temp="(evento) => (estado.tarefaTemp = evento.target.value)"
      :cadastra-taterefa="cadastraTarefa"
    />

    <!-- Componente ListaDeTarefas recebe como prop as tarefas filtradas.
         Também escuta o evento 'deletar' emitido pelo componente filho,
         chamando a função deletarTarefa para remover a tarefa. -->
    <ListaDeTarefas :tarefas="getTarefasfiltradas()" @deletar="deletarTarefa" />
  </div>
</template>

<style scoped>
/* Estilo aplicado ao container principal:
   - largura máxima de 900px
   - centralizado com margin auto
   - padding interno para espaçamento
   - bordas arredondadas
   - fundo com gradiente suave usando as cores históricas (azul, púrpura e escarlate)
   - sombra para dar profundidade */
.container {
  max-width: 900px;
  margin: 40px auto;
  padding: 30px;
  border-radius: 12px;
  background: linear-gradient(
    135deg,
    rgba(0, 71, 171, 0.1),
    /* Azul Tekhelet suave */ rgba(128, 0, 128, 0.08),
    /* Púrpura Argaman suave */ rgba(255, 36, 0, 0.08) /* Escarlate suave */
  );
  box-shadow: 0 6px 15px rgba(0, 0, 0, 0.15);
}

/* Tipografia aplicada ao título e parágrafo dentro do container */
.container h1,
.container p {
  font-family: "Segoe UI", sans-serif;
}

/* Espaçamento entre os componentes filhos dentro do container */
.container > * {
  margin-bottom: 20px;
}
</style>
