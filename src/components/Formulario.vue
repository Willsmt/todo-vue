<script setup>
const props = defineProps([
  "cadastraTaterefa",
  "tarefaTemp",
  "trocarFiltro",
  "editaTarefaTemp",
]);
</script>

<template>
  <form @submit.prevent="props.cadastraTaterefa">
    <div class="row">
      <div class="col">
        <input
          :value="props.tarefaTemp"
          @change="props.editaTarefaTemp"
          required
          type="text"
          placeholder="Digite aqui a Drescrição da terafa"
          class="form-control"
        />
      </div>
      <div class="col-md-2">
        <button type="submit" class="btn btn-primary">Cadastrar</button>
      </div>
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
.formulario {
  margin-top: 20px;
  padding: 15px;
  background: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

/* Input */
.form-control {
  border: 2px solid #0047ab; /* Azul Tekhelet */
  transition: all 0.3s ease;
}

.form-control:focus {
  border-color: #800080; /* Púrpura Argaman */
  box-shadow: 0 0 6px rgba(128, 0, 128, 0.4);
}

/* Botão */
.btn-primary {
  background-color: #0047ab; /* Azul */
  border-color: #0047ab;
  font-weight: bold;
  transition: background-color 0.3s ease;
}

.btn-primary:hover {
  background-color: #601ef9; /* Violeta/Azul */
  border-color: #601ef9;
}

/* Select */
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
