


# 📘 Projeto de Estudos - Lista de Tarefas (Vue 3)

Este projeto é uma aplicação simples de **Lista de Tarefas (To-Do List)** desenvolvida em **Vue 3** utilizando a sintaxe do `<script setup>`.  
O objetivo é servir como material de estudo para entender conceitos fundamentais do Vue, como **componentização, props, eventos, estado reativo e estilização**.

---

## 🚀 Funcionalidades

- ✅ Cadastrar novas tarefas  
- ✅ Marcar tarefas como concluídas  
- ✅ Filtrar tarefas (todas, pendentes, finalizadas)  
- ✅ Excluir tarefas  
- ✅ Interface estilizada com cores históricas (Azul Tekhelet, Púrpura Argaman e Escarlate Tola'at Shani)  

---

## 🏗️ Estrutura do Projeto

O projeto é dividido em **componentes**:

- **App.vue** → Componente raiz que gerencia o estado global e conecta os filhos.  
- **Cabecalho.vue** → Exibe o título e a quantidade de tarefas pendentes.  
- **Formulario.vue** → Permite cadastrar novas tarefas e escolher o filtro.  
- **ListaDeTarefas.vue** → Exibe as tarefas filtradas, permite marcar como concluídas e excluir.  

---

## 🎨 Paleta de Cores Históricas

Inspirada em cores mencionadas em textos antigos:

- **Azul Tekhelet** → `#0047AB`  
- **Púrpura Argaman** → `#800080`  
- **Escarlate Tola'at Shani** → `#FF2400`  

Essas cores foram aplicadas em gradientes e detalhes visuais para dar identidade ao projeto.

---

## ⚙️ Tecnologias Utilizadas

- [Vue 3](https://vuejs.org/)  
- [Bootstrap](https://getbootstrap.com/) (para layout e classes utilitárias)  
- HTML5 / CSS3  

---

## ▶️ Como Rodar o Projeto

1. Clone este repositório:
   ```bash
   git clone https://github.com/seu-usuario/nome-do-repositorio.git
  

2. Acesse a pasta do projeto:
   ```bash
   cd nome-do-repositorio
   ```

3. Instale as dependências:
   ```bash
   npm install
   ```

4. Rode o servidor de desenvolvimento:
   ```bash
   npm run dev
   ```

5. Abra no navegador:
   ```
   http://localhost:5173
   ```

---

## 📚 Objetivo

Este projeto foi criado **para fins de estudo**.  
Ele serve como base para revisar:
- Uso de **props** e **emits** entre componentes.  
- Manipulação de **estado reativo** com `reactive`.  
- Estruturação de **componentes independentes**.  
- Aplicação de **estilos customizados** com cores históricas.  

---

## ✨ Próximos Passos

- Implementar persistência das tarefas com **localStorage**.  
- Adicionar animações para transições de tarefas.  
- Criar testes unitários com **Vitest**.  

---

## 📌 Licença

Este projeto é apenas para **estudos pessoais** e não possui fins comerciais.  
Sinta-se livre para clonar, modificar e aprender com ele!
