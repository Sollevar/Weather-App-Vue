<script setup>
const props = defineProps({
    error: String,
})
</script>
<template>
    <div v-if="error" class="error">
        {{ props.error }}
    </div>
</template>
<style scoped>
.error {
    position: absolute;
    top: 0;
    align-self: center;
    padding: 20px 50px;
    font-size: 18px;
    border-bottom-left-radius: 25px;
    border-bottom-right-radius: 25px;
    background-color: var(--card-background-color);
    text-align: center;
}
</style>