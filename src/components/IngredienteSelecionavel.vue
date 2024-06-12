<script lang="ts">
import Tag from './Tag.vue';

export default {
    props: {
        ingrediente: { type: String, required: true }
    },
    data() {
        return {
            selecionado: false
        }
    },
    components: { Tag },
    methods:{
        aoClicar(){
            this.selecionado = !this.selecionado;
            
            if(this.selecionado){
                this.$emit('adicionarIngrediente', this.ingrediente);
            }
            else{
                this.$emit('removerIngrediente', this.ingrediente);
            }
        }
    },
    emits: ['adicionarIngrediente', 'removerIngrediente'], //recebe quais eventos o componente pode emitir
}
</script>

<template>
    <button class="ingrediente" @click="aoClicar()" :aria-pressed="selecionado"> <!-- @ é igual a v-on: -->
        <Tag :texto="ingrediente" :ativa="selecionado" />
    </button>
</template>

<style scoped>
.ingrediente {
    cursor: pointer;
}
</style>