<script setup>
import FormLoginVue from "./components/FormLogin.vue";
import ResultFormVue from "./components/ResultForm.vue";
</script>

<template>
<div class="body">
    <FormLoginVue/>
    <ResultFormVue/>
</div>
</template>

<style scoped>
.body {
    display: flex;
    flex-direction: column;
    background-color: #474747;
    height: 100vh;
    font-family: monospace !important;
    justify-content: center;
}
</style>