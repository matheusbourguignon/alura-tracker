<template>
<div class="box has-text-weight-bold" :style="estilos">
<!-- slot- riamos um componente para representar o Box. Assim, conseguimos exibir os elementos filhos dentro do nosso Box.  -->
<slot> </slot>
</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
name: 'box',
data () {
return {
    estilos:{
    backgroundColor: '#FAF0CA'
    }
}    
}
})
</script>
