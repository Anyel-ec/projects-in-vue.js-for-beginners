<script setup>
import { ref } from 'vue';
import { defineEmits } from 'vue';
const text = ref("");
const emits = defineEmits(["onNewItem"]);
function handleSubmit(e) {
    if (text.value !== "") {
        emits("onNewItem", text.value); 
        text.value = "";
    }
}
</script>


<template>
<form action="" @submit.prevent="handleSubmit">
    <input type="text" v-bind="text" >
</form>
</template>


<style scoped>
</style>