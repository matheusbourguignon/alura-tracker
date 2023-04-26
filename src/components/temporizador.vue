<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">

        <cronometro :tempoEmSegundos="tempoEmSegundos" />
         <!-- atributos do botão quando adiciono o valor vai tá linkcado com meu atributo':
         'disabled="!cronometroRodando @click é um evento usado no botão -->
        <button class="button" @click="iniciar" :disabled="cronometroRodando">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>
         <!-- atributos do botão quando adiciono o valor vai tá linkcado com meu atributo':
        'disabled="!cronometroRodando @click é um evento usado no botão -->
        <button class="button" @click="finalizar" :disabled="!cronometroRodando">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>

    </div>
</template>
<script lang="ts">

import { defineComponent } from 'vue';
import cronometro from './cronometro.vue';

export default defineComponent({
    name: 'temporizador', 
    emits: ['aoTemporizadorFinalizado'], /* uma lista de eventos que é capaz de emitir */
    components: {
     cronometro
    },
    data() {
        return {
            //propriedades
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        }
    },

    methods: {
        iniciar() {
            //começar a contagem
            // 1 seg = 1000 ms
            this.cronometroRodando = true
            this.cronometro = setInterval(() => {
                //componente
                this.tempoEmSegundos += 1
            }, 1000)
        },
        finalizar() {
            clearInterval(this.cronometro)
            this.cronometroRodando = false

            /*this.$emit é um metado que vai receber 2 parâmentros. 1- 'aoTemporizadorFinalizado', 2- panloud a carga de dados que vai junto no caso this.TemposEmSegundos */
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos) 
            this.tempoEmSegundos = 0;
            
        }
    }
})
</script>          