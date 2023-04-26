<template>

  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <barraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <formulario @aoSalvarTarefa="salvarTarefa"/>
     <!-- lista de tarefas -->
     <div class="lista">
      <tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
      <!-- v-if é usada para renderizar condicionalmente um bloco -->
      <box v-if="listaEstaVazia"> 
       Você não está muito produtivo hoje :(
      </box>
    </div>
  </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import barraLateral from './components/barraLateral.vue';
import formulario from './components/formulario.vue';
import tarefa from './components/tarefa.vue';
import box from './components/box.vue';
import iTarefa from './interfaces/iTarefa'


export default defineComponent({
  name: 'App',
  components: {
    barraLateral, 
    formulario, 
    tarefa,
    box
    
  },

  data() {  
  return{
    tarefas: [] as iTarefa[],
    modoEscuroAtivo: false
  
    }   
  },

  computed:{
  listaEstaVazia () : boolean{
  return this.tarefas.length === 0
    
    }
  },
  methods:{
  /* esse metado vai receber uma tarefa por parâmetro */
  salvarTarefa (tarefa: iTarefa){
    this.tarefas.push(tarefa)
    },
    trocarTema (modoEscuroAtivo: boolean) {
    this.modoEscuroAtivo = modoEscuroAtivo
    }
  }

});
</script>

<style>
.lista{
  padding: 1.25rem;
}

main{
  --bg-primario: #fff;
  --texto-primario: #000;
}

main.modo-escuro{
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}
.conteudo{
  background-color: var(--bg-primario);
}

</style>
