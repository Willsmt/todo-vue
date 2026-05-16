<script setup>
const props = defineProps(["tarefasPendentes"]);
</script>

<template>
  <header class="cabecalho p-5 mb-4 mt-4 rounded-3 text-white">
    <h1>Minhas tarefas</h1>
    <p>Você possui {{ props.tarefasPendentes }} tarefas pendentes</p>
  </header>
</template>

<style scoped>
.cabecalho {
  /* Gradiente com as três cores */
  background: linear-gradient(135deg, #0047ab, #800080, #ff2400);
  color: #fff;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
}

/* Título com destaque */
.cabecalho h1 {
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 2px;
}

/* Texto secundário */
.cabecalho p {
  font-size: 1.2rem;
  margin-top: 10px;
}
</style>
