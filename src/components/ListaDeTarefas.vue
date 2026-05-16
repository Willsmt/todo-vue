<script setup>
// <script setup> simplifica a sintaxe do Vue 3.
// Aqui declaramos as props e eventos que o componente recebe.

// Props:
// - tarefas: lista de tarefas que será exibida na tela.
const props = defineProps(["tarefas"]);

// Emits:
// - deletar: evento que será disparado quando o usuário clicar no botão "Excluir".
const emit = defineEmits(["deletar"]);
</script>

<template>
  <!-- Lista de tarefas -->
  <!-- v-if: só renderiza a lista se houver pelo menos uma tarefa -->
  <ul class="list-group mt-4" v-if="props.tarefas.length > 0">
    <!-- v-for: percorre todas as tarefas recebidas via props -->
    <!-- :key: ajuda o Vue a identificar cada item de forma única -->
    <li
      class="list-group-item d-flex justify-content-between align-items-center"
      v-for="tarefa in props.tarefas"
      :key="tarefa.titulo"
    >
      <div>
        <!-- Checkbox para marcar se a tarefa está finalizada -->
        <!-- :checked: valor inicial vem da propriedade finalizada -->
        <!-- @change: atualiza o estado da tarefa quando o usuário marca/desmarca -->
        <input
          :checked="tarefa.finalizada"
          :id="tarefa.titulo"
          type="checkbox"
          @change="(evento) => (tarefa.finalizada = evento.target.checked)"
        />

        <!-- Label que mostra o título da tarefa -->
        <!-- :class: aplica a classe "done" se a tarefa estiver finalizada -->
        <!-- :for: associa o label ao checkbox pelo id -->
        <label
          :class="{ done: tarefa.finalizada }"
          class="ms-3"
          :for="tarefa.titulo"
        >
          {{ tarefa.titulo }}
        </label>
      </div>

      <!-- Botão de deletar -->
      <!-- ms-auto: empurra o botão para o final da linha -->
      <!-- @click: emite o evento "deletar" passando a tarefa como parâmetro -->
      <button
        class="btn btn-danger btn-sm ms-auto"
        @click="emit('deletar', tarefa)"
      >
        Excluir
      </button>
    </li>
  </ul>

  <!-- Mensagem alternativa -->
  <!-- v-else: aparece quando não há tarefas na lista -->
  <p v-else class="mt-4 text-muted">Não há tarefas pendentes.</p>
</template>

<style scoped>
/* Estilo da lista principal */
.list-group {
  border-radius: 8px; /* bordas arredondadas */
  overflow: hidden; /* evita que elementos saiam do container */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* sombra leve */
}

/* Cada item da lista */
.list-group-item {
  background: #fdfdfd; /* fundo branco */
  border: none; /* remove borda padrão */
  border-bottom: 1px solid #eee; /* separação entre itens */
  transition: background-color 0.3s ease; /* animação suave */
}

/* Efeito hover: muda cor ao passar o mouse */
.list-group-item:hover {
  background-color: #f5f5ff; /* leve azul */
}

/* Checkbox estilizado */
input[type="checkbox"] {
  accent-color: #0047ab; /* Azul Tekhelet */
  transform: scale(1.2); /* aumenta o tamanho */
  cursor: pointer; /* cursor de mão */
}

/* Texto da tarefa */
label {
  font-size: 1rem;
  color: #333;
  transition: color 0.3s ease;
}

/* Quando a tarefa está finalizada */
.done {
  text-decoration: line-through; /* risca o texto */
  color: #800080; /* Púrpura Argaman */
}

/* Botão excluir */
.btn-danger {
  background-color: #c62d25; /* Escarlate */
  border-color: #c62d25;
  font-weight: bold;
  transition: background-color 0.3s ease;
}

/* Hover do botão excluir */
.btn-danger:hover {
  background-color: #ff2400; /* Escarlate vivo */
  border-color: #ff2400;
}
</style>
