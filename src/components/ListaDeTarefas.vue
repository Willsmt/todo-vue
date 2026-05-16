<script setup>
const props = defineProps(["tarefas"]);
</script>

<template>
  <ul class="list-group mt-4" v-if="props.tarefas.length > 0">
    <li
      class="list-group-item"
      v-for="tarefa in props.tarefas"
      :key="tarefa.titulo"
    >
      <input
        :checked="tarefa.finalizada"
        :id="tarefa.titulo"
        type="checkbox"
        @change="(evento) => (tarefa.finalizada = evento.target.checked)"
      />
      <label
        :class="{ done: tarefa.finalizada }"
        class="ms-3"
        :for="tarefa.titulo"
      >
        {{ tarefa.titulo }}
      </label>
    </li>
  </ul>

  <!-- Mensagem alternativa -->
  <p v-else class="mt-4 text-muted">Não há tarefas pendentes.</p>
</template>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>
