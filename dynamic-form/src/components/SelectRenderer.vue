<script setup>
defineProps(['modelValue','selections'])
const emit=defineEmits(['update:modelValue'])
</script>

<template>
<select :value="modelValue" @change="emit('update:modelValue',$event.target.value)" >
    <option v-for="item in selections" :key="item.value" :value="item.value">{{ item.selection }}</option>
</select>
</template>

<style scoped></style>