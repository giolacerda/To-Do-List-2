<script lang="ts">
import ItensTarefa from './components/ItensTarefa.vue';

export default{
  data() {
    return{
      listaDeTarefas: [
        {nome: "Estudar vue.js",
          descricao: "Praticar diretivas (v-for, v-if) e entender melhor props e emits.",
          data: "24/09/2025",
          prioridade: "Alta"
        },
        {nome: "Exercício Físico",
         descricao: "Fazer 30 minutos de caminhada ou corrida leve.",
         data: "24/09/2025",
         prioridade: "Média"

        },
        {nome: "Organizar Espaço de Trabalho",
         descricao: "Arrumar mesa, cabos e pastas para manter o ambiente limpo e organizado.",
         data: "24/09/20250",
         prioridade: "Baixa"
        },
        {nome: "Preparar Conteúdo para Redes",
         descricao: "Criar um post sobre dicas de programação para o Instagram.",
         data: "24/29/2025",
         prioridade: "Média"
        }
      ],
       mensagem: ""
    }
  },

  methods: {
    concluirTarefa(tarefa: any) {
      console.log ("Tarefa concluída", tarefa)
      this.mensagem = `Parabéns! Você concluiu a tarefa: ${tarefa.nome}`
    }
  },

  components: {ItensTarefa}

}
</script>

<template>
  <div class="corpo__card">
  <ItensTarefa v-for="(item, index) in listaDeTarefas"
  :key="index"
  :tarefas="item"
  @tarefa-selecionada="concluirTarefa"
  />
  </div>
  <div v-if="mensagem">
    <h1>{{ mensagem }}</h1>
  </div>
</template>


<style scoped>
body {
  margin: 0;
  padding: 0;
  font-family: 'Poppins', sans-serif;
  background: linear-gradient(135deg, #ff9a9e, #fad0c4, #fad0c4, #fbc2eb, #a18cd1);
  background-size: 400% 400%;
  animation: gradientAnimation 12s ease infinite;
}

@keyframes gradientAnimation {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

.corpo__card {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 20px;
  padding: 30px;
}

h1 {
  text-align: center;
  font-size: 2rem;
  margin-top: 20px;
  color:  #ff9f1c;
  text-shadow: 2px 2px 8px rgba(0,0,0,0.3);
}

</style>
