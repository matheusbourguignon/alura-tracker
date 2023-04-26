<template>
    <box>
    <div class="columns">
        <div class="column is-7">
           {{tarefa.descricao || 'Tarefa sem Descrição'}}
        </div>

        <div class="column">
            <cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
        </div>
    </div>
</box> 
</template> 

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import cronometro from './cronometro.vue';
import iTarefa from '../interfaces/iTarefa';
import box from './box.vue';

export default defineComponent({    
name: "tarefa",
components: {
    cronometro,
    box
},
props:{
    tarefa: {
         type: Object as PropType <iTarefa>,
         required: true
         
    }
  }
})
</script>

