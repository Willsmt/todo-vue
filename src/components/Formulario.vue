<script setup>
// Usamos <script setup>, que simplifica a sintaxe do Vue 3.
// Aqui declaramos as props que o componente vai receber do pai (App.vue).
// São funções e valores que controlam o comportamento do formulário:
// - cadastraTaterefa: função que cadastra uma nova tarefa.
// - tarefaTemp: valor temporário digitado no input.
// - trocarFiltro: função que altera o filtro (todas, pendentes, finalizadas).
// - editaTarefaTemp: função que atualiza o valor do input conforme o usuário digita.
const props = defineProps([
  "cadastraTaterefa",
  "tarefaTemp",
  "trocarFiltro",
  "editaTarefaTemp",
]);
</script>
<template>
  <!-- Formulário principal -->
  <!-- @submit.prevent: impede o comportamento padrão de recarregar a página e chama a função props.cadastraTaterefa para cadastrar a tarefa -->

  <form @submit.prevent="props.cadastraTaterefa">
    <div class="row">
      <!-- Coluna com o campo de texto -->
      <div class="col">
        <!-- Valor do input vem da prop tarefaTemp -->
        <!-- Atualiza tarefaTemp quando o usuário digita -->
        <!-- Campo obrigatório -->
        <input
          :value="props.tarefaTemp"
          @change="props.editaTarefaTemp"
          required
          type="text"
          placeholder="Digite aqui a Drescrição da terafa"
          class="form-control"
        />
      </div>

      <!-- Coluna com o botão de cadastrar -->
      <div class="col-md-2">
        <button type="submit" class="btn btn-primary">Cadastrar</button>
      </div>

      <!-- Coluna com o select para escolher o filtro -->
      <div class="col-md-2">
        <select @change="props.trocarFiltro" class="form-control">
          <option value="todas">Todas Tarefas</option>
          <option value="pendentes">Pendentes</option>
          <option value="finalizadas">Finalizadas</option>
        </select>
      </div>
    </div>
  </form>
</template>

<style scoped>
/* Estilo geral do formulário */
.formulario {
  margin-top: 20px;
  padding: 15px;
  background: #f9f9f9; /* fundo claro */
  border-radius: 8px; /* bordas arredondadas */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* sombra leve */
}

/* Input estilizado */
.form-control {
  border: 2px solid #0047ab; /* Azul Tekhelet */
  transition: all 0.3s ease; /* animação suave ao focar */
}

.form-control:focus {
  border-color: #800080; /* Púrpura Argaman */
  box-shadow: 0 0 6px rgba(128, 0, 128, 0.4);
}

/* Botão de cadastrar */
.btn-primary {
  background-color: #0047ab; /* Azul Tekhelet */
  border-color: #0047ab;
  font-weight: bold;
  transition: background-color 0.3s ease;
}

.btn-primary:hover {
  background-color: #601ef9; /* Violeta/Azul */
  border-color: #601ef9;
}

/* Select estilizado */
.form-select {
  border: 2px solid #c62d25; /* Escarlate */
  color: #c62d25;
  transition: all 0.3s ease;
}

.form-select:focus {
  border-color: #ff2400; /* Escarlate mais vivo */
  box-shadow: 0 0 6px rgba(255, 36, 0, 0.4);
}
</style>
