<script>
export default{
    data(){
        return{
            currenValue: "",
            tag: []
        }
    },
}
</script>

<template>
    <div class="input-tag">
      <div class="tags">
        <div class="tag" v-for="(tag, index) in tag" :key="index">{{ tag }}</div>
      </div>
      <input type="text" v-model="currentValue" />
    </div>
  </template>
  


<style scoped></style>