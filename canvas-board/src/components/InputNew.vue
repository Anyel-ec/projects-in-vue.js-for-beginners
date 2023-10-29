<script setup>
import { ref } from 'vue/reactivity';
const text = ref("");

const handleSubmit = (e) => {
    if (text.value !== "") {
        console.log(text.value);
        text.value = "";
    }
}

</script>




<template> 
<form action="" @submit.prevent="handleSubmit"></form>
    <input type="text" v-bind="text">
</template>




<style scoped></style>