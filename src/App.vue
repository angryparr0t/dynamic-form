<script setup>
import {ref} from 'vue'
import dynamicForm from './components/DynamicForm.vue'
const config= [
  {
    "name": "username",
    "type": "text",
    "rule": {"required": "required"},
  },
  {
    "name": "userid",
    "type": "text",
    "rule": {"required":"required","maxLength":"6"},

  },
  {
    "name": "date",
    "type": "date-range",
    "rule": { "required": "required" },


  },
  {
    "name": "gender",
    "type": "select",
    "props": {
      "selections": [
        { "value": "male", "selection": "male" },
        { "value": "female", "selection": "female" }
      ]
    },
    "rule": { "required": "required" },


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
