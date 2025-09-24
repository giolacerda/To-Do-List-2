<script lang="ts">
export default {
    props: {
        tarefas: { type: Object, required: true }
    },
    methods: {
        tarefaClicada() { this.$emit('tarefa-selecionada', this.tarefas) }
    }

}

</script>

<template>
    <section class="card" @click="tarefaClicada">
        <h1>{{ tarefas.nome }}</h1>
        <p>{{ tarefas.descricao }}</p>
        <p>{{ tarefas.prioridade }}</p>
        <p>{{ tarefas.data }}</p>
    </section>


</template>

<style scoped>
.card {
  background: white;
  border-radius: 16px;
  padding: 20px;
  box-shadow: 0 6px 20px rgba(0,0,0,0.1);
  cursor: pointer;
  transition: transform 0.3s ease, box-shadow 0.3s ease, background 0.3s ease;
}

.card:hover {
  transform: scale(1.05);
  background: linear-gradient(135deg, #f6d365 0%, #fda085 100%);
  box-shadow: 0 12px 30px rgba(0,0,0,0.2);
  color: white;
}

.card h1 {
  font-size: 1.5rem;
  margin-bottom: 10px;
}

.card p {
  margin: 6px 0;
  font-size: 0.95rem;
}

/* prioridade colorida */
.card p:nth-child(3) {
  font-weight: bold;
}

.card p:contains("Alta") {
  color: #ff4d6d;
}

.card p:contains("Média") {
  color: #ff9f1c;
}

.card p:contains("Baixa") {
  color: #2ec4b6;
}
</style>
