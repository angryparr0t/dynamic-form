<script setup>
import {ref} from 'vue'
import dynamicForm from './components/DynamicForm.vue'
const config=ref([
  {name:'username',
  type:'text'},

  {name:'userid',
  type:'text'},

  {name:'date',
  type:'date-range'},

  {name:'gender',
  type:'select',
  props:{
    selections:[
    {value:'male',selection:'male'},
    {value:'female',selection:'female'}]
  }}
])

</script>

<template>
 
<dynamicForm :formConfig="config"/>
</template>

<style scoped>

</style>
