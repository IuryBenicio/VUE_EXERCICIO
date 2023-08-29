<script setup>
    const props = defineProps(['total', 'select_evento', 'numA_evento', 'numB_evento', 'estado_numA', 'estado_filtro', 'estado_numB'])
</script>
<template>
    <div class="display mb-2 rounded">
        {{ props.total }}
    </div>
    <div class="input-group">
        <span class="input-group-text">Primeiro número</span>
        <input @keyup="props.numA_evento" type="text" class="form-control">
        <span class="input-group-text">operação</span>
        <select @change="props.select_evento" class="form-control">
            <option value="selecionar">selecionar</option>
            <option value="+">+</option>
            <option value="*">*</option>
            <option value="/">/</option>
            <option value="-">-</option>
        </select>
        <span class="input-group-text">Segundo número</span>
        <input @keyup="props.numB_evento" type="text" class="form-control">
        </div>
    {{ props.estado_numA +'  '+props.estado_filtro+'  '+ props.estado_numB + ' = '+ props.total}}
</template>

<style scoped>
    .display{
        text-align: center;
        font-size: 20px;
        width: 100%;
        padding: 4px;
        background-color: rgb(189, 189, 189);
    }
</style>