<template>
  <form @submit.prevent=handleSubmit>
    
    <div v-for="item in formConfig" :key="item.name">
    
      <label :for="item.name">{{ item.name }}</label>
      <component :is="getComponent(item.type)"
      v-model="formData[item.name]"
      v-bind="item.props" 
      />
    </div>
    <slot name="submit">
      <button @click="handleSubmit">submit</button>
    </slot>
  </form>
</template>

<script setup>
import {reactive, ref}  from 'vue'
import textRenderer from './TextRenderer.vue'
import selectRenderer from './SelectRenderer.vue'
import dateRenderer from './DateRenderer.vue'
const formData=reactive({})
const props = defineProps({
  formConfigJSON:{
    type:String,
    required:true,
    validator: (configJSON) =>{
      const config=JSON.parse(configJSON)
      return config.every((i)=>'name' in i && 'type' in i)
    }, 
  }
})

const formConfig=ref(JSON.parse(props.formConfigJSON))

const componentTypeMap={
  'text':textRenderer,
  'select':selectRenderer,
  'date-range':dateRenderer,
}
const getComponent=(type)=>{
  return componentTypeMap[type]
}

const handleSubmit = () => {
  console.log('Form submitted:', formData)
}

</script>



<style scoped>
form {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

div {
  margin-bottom: 20px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

label {
  font-weight: 500;
  color: #333;
  font-size: 14px;
}

input, select {
  padding: 8px 12px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 14px;
  width: 100%;
  box-sizing: border-box;
}

input:focus, select:focus {
  outline: none;
  border-color: #409eff;
  box-shadow: 0 0 0 2px rgba(64, 158, 255, 0.1);
}

button {
  padding: 10px 20px;
  background-color: #409eff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 14px;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #66b1ff;
}
</style>
