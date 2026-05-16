<script setup>
// Aqui usamos o <script setup>, que é a forma simplificada de declarar lógica em componentes Vue 3.
// Com ele, não precisamos escrever "export default" nem retornar nada manualmente.

// defineProps: função do Vue que declara quais propriedades (props) o componente recebe.
// Nesse caso, o componente espera receber "tarefasPendentes" do pai (App.vue).
const props = defineProps(["tarefasPendentes"]);
</script>

<template>
  <!-- O cabeçalho principal do app -->
  <header class="cabecalho p-5 mb-4 mt-4 rounded-3 text-white">
    <!-- Título fixo -->
    <h1>Minhas tarefas</h1>
    <!-- Texto dinâmico que mostra quantas tarefas pendentes existem.
         Usamos props.tarefasPendentes para acessar o valor passado pelo componente pai. -->
    <p>Você possui {{ props.tarefasPendentes }} tarefas pendentes</p>
  </header>
</template>

<style scoped>
/* Classe cabecalho aplicada ao <header>.
   Aqui criamos um fundo com gradiente usando as três cores históricas:
   - Azul Tekhelet (#0047AB)
   - Púrpura Argaman (#800080)
   - Escarlate Tola'at Shani (#FF2400)
   Também aplicamos sombra para dar profundidade. */
.cabecalho {
  background: linear-gradient(135deg, #0047ab, #800080, #ff2400);
  color: #fff; /* Texto branco para contraste */
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
}

/* Estilo para o título (h1):
   - Negrito
   - Letras maiúsculas
   - Espaçamento entre caracteres para dar impacto visual */
.cabecalho h1 {
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 2px;
}

/* Estilo para o parágrafo (p):
   - Fonte um pouco maior
   - Espaçamento superior para separar do título */
.cabecalho p {
  font-size: 1.2rem;
  margin-top: 10px;
}
</style>
