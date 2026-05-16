<script setup>
import { reactive } from "vue";
import Cabecalho from "./components/Cabecalho.vue";
import Formulario from "./components/Formulario.vue";
import ListaDeTarefas from "./components/ListaDeTarefas.vue";

const estado = reactive({
  filtro: "todas",
  tarefaTemp: "",
  tarefas: [],
});

const getTarefasPendentes = () => {
  return estado.tarefas.filter((tarefa) => !tarefa.finalizada);
};
const getTarefasFinalizadas = () => {
  return estado.tarefas.filter((tarefa) => tarefa.finalizada);
};

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

const cadastraTarefa = () => {
  const tarefaNova = {
    titulo: estado.tarefaTemp,
    finalizada: false,
  };

  estado.tarefas.push(tarefaNova);
  estado.tarefaTemp = "";
};

const deletarTarefa = (tarefa) => {
  estado.tarefas = estado.tarefas.filter((t) => t !== tarefa);
};
</script>

<template>
  <div class="container">
    <Cabecalho :tarefas-pendentes="getTarefasPendentes().length" />
    <Formulario
      :trocar-filtro="(evento) => (estado.filtro = evento.target.value)"
      :tarefa-temp="estado.tarefaTemp"
      :edita-tarefa-temp="(evento) => (estado.tarefaTemp = evento.target.value)"
      :cadastra-taterefa="cadastraTarefa"
    />
    <ListaDeTarefas :tarefas="getTarefasfiltradas()" @deletar="deletarTarefa" />
  </div>
</template>

<style scoped>
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

.container h1,
.container p {
  font-family: "Segoe UI", sans-serif;
}

.container > * {
  margin-bottom: 20px;
}
</style>
