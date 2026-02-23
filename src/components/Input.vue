<script setup>
const model = defineModel({ type: String });
</script>

<template>
    <input v-model="model" type="text" class="input" />
</template>

<style scoped>
.input {
    padding: 10px 10px 10px 20px;
    border-radius: 10px;
    border: none;
    font-size: 18px;
    color: var(--primary-color);
    background-color: var(--card-background-color);
    box-shadow: 1px 2px 4px 0px var(--app-color);
}

.input::placeholder {
    color: var(--placeholder-text-color);
}
</style>