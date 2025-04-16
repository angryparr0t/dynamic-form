<script setup>
import {ref} from 'vue'
import dynamicForm from './components/DynamicForm.vue'
const config= [
  {
    "name": "username",
    "type": "text"
  },
  {
    "name": "userid",
    "type": "text"
  },
  {
    "name": "date",
    "type": "date-range"
  },
  {
    "name": "gender",
    "type": "select",
    "props": {
      "selections": [
        { "value": "male", "selection": "male" },
        { "value": "female", "selection": "female" }
      ]
    }
  }
];
//JSON.stringify(config) 会把 config 对象转换为符合 JSON 格式的字符串
const configJSON= JSON.stringify(config)
</script>

<template>
 
<dynamicForm :formConfigJSON="configJSON"/>
</template>

<style scoped>

</style>
