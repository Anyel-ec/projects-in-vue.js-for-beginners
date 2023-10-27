<script>
import { toHandlerKey } from 'vue';

export default {
  data() {
    return {
      currentValue: "",
      tag: []
    }
  },
  methods: {
    handleKeyDown(e) {
  const key = toHandlerKey(e);
  if (key === "backspace") {
    if (typeof this.currentValue === 'string') {
      if (this.currentValue === "" && this.tag.length > 0) {
        this.tag.pop();
      } else if (this.currentValue !== "") {
        this.currentValue = this.currentValue.slice(0, -1);
      }
    }
  }
},



    handleSubmit(e) {
      e.preventDefault();
      if (this.currentValue !== "") {
        const exist = this.tag.some(t => t === this.currentValue);
        if (!exist) {
          this.tag.push(this.currentValue);
          this.currentValue = "";
        }
      }
    },
    deleteTag(tag) {
      this.tag = this.tag.filter(t => t !== tag);
    }
  }
}
</script>

<template>
  <div class="input-tag">
    <div class="tags">
      <div class="tag" v-for="(tag, index) in tag" :key="index">{{ tag }}
        <button @click="deleteTag(tag)">x</button>
      </div>
    </div>
    <form @submit.prevent="handleSubmit">
        <input type="text" v-model="currentValue" @keyup="handleKeyDown"/>

    </form>
  </div>
</template>


<style scoped>
input {
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 5px;
  width: 100%;
  box-sizing: border-box;
  outline: none;
}
.tags{
    display: flex;
    gap: 3;
    padding: 3px;
}
.tags .tag{
    display: flex;
    align-items: center;
    gap: 3px;
    padding: 3px;
    border: 1px solid #ccc;
    border-radius: 5px;
    
}
</style>