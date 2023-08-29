<script setup>
    const props = defineProps(['getoperacao', 'reseta'])
</script>
<template>
    <div class="botoes">
        <button @click="props.getoperacao" type="button" class="btn btn-success mt-2">=</button>
        <button @click="props.reseta" type="reset" class="mt-2 btn btn-secondary">Resetar</button>
    </div>
</template>

<style scoped>
    .botoes{
        display: flex;
        justify-content: space-between;
    }
    .btn{
        width: 49.5%;
    }
</style>