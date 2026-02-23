<script setup>
</script>
<template>
    <button class="button">
        <slot/>
    </button>
</template>
<style scoped>
.button {
    display: flex;
    gap: 8px;
    width: 100%;
    align-items: center;
    justify-content: center;
    padding: 14px;
    border: none;
    border-radius: 10px;
    font-family: var(--font);
    font-weight: 600;
    font-size: 20px;
    cursor: pointer;
    color: var(--primary-color);
    background: var(--gradient-color);
    transition: background 0.3s ease-in-out;
}

.button:hover{
    background: var(--inverted-gradient-color);
}
</style>