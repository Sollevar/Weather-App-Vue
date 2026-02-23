<script setup>
const { label, value} = defineProps({
    label:String,
    value:{
        type: String,
        default: 'Неизвестно'
    },
});
</script>
<template>
    <dl class="statistic">
        <div class="statistic__item">
            <dt class="statistic__name">
                {{ label }}
            </dt>
            <dd class="statistic__value">
                {{ value }}
            </dd>
        </div>
    </dl>
</template>
<style scoped>
.statistic {
    margin: 0;
    display: flex;
    flex-direction: column;
}

.statistic__item {
    font-size: 28px;
    display: flex;
    justify-content: space-between;
}

.statistic__name {
    font-weight: 700;
    text-transform: uppercase;
}

.statistic__value {
    font-weight: 500;
}
</style>