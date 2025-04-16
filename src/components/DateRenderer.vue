<script setup>
defineProps(['modelValue'])
const emit=defineEmits('update:modelValue')
</script>

<template>
 
    <input type="date" :value="modelValue" @input="$emit('update:modelValue',$event.target.value)">
    

</template>

<style scoped></style>