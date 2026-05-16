<script setup>
const props = defineProps(["tarefas"]);
const emit = defineEmits(["deletar"]);
</script>

<template>
  <ul class="list-group mt-4" v-if="props.tarefas.length > 0">
    <li
      class="list-group-item d-flex justify-content-between align-items-center"
      v-for="tarefa in props.tarefas"
      :key="tarefa.titulo"
    >
      <div>
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
      </div>

      <!-- Botão de deletar alinhado à direita -->
      <button
        class="btn btn-danger btn-sm ms-auto"
        @click="emit('deletar', tarefa)"
      >
        Excluir
      </button>
    </li>
  </ul>

  <!-- Mensagem alternativa -->
  <p v-else class="mt-4 text-muted">Não há tarefas pendentes.</p>
</template>

<style scoped>
/* Estilo da lista */
.list-group {
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

/* Cada item */
.list-group-item {
  background: #fdfdfd;
  border: none;
  border-bottom: 1px solid #eee;
  transition: background-color 0.3s ease;
}

/* Hover */
.list-group-item:hover {
  background-color: #f5f5ff; /* leve azul */
}

/* Checkbox */
input[type="checkbox"] {
  accent-color: #0047ab; /* Azul Tekhelet */
  transform: scale(1.2);
  cursor: pointer;
}

/* Texto da tarefa */
label {
  font-size: 1rem;
  color: #333;
  transition: color 0.3s ease;
}

/* Quando finalizada */
.done {
  text-decoration: line-through;
  color: #800080; /* Púrpura Argaman */
}

/* Botão excluir */
.btn-danger {
  background-color: #c62d25; /* Escarlate */
  border-color: #c62d25;
  font-weight: bold;
  transition: background-color 0.3s ease;
}

.btn-danger:hover {
  background-color: #ff2400; /* Escarlate vivo */
  border-color: #ff2400;
}
</style>
