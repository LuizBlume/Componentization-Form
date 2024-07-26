<template>
    <div class="body">
      <FormLoginVue :produto="elementForms" @validarFormulario="validarFormulario" />
      <ResultFormVue v-if="validado" :resultado="resultado" />
    </div>
  </template>
  
  <script setup>
  import { reactive, ref } from "vue";
  import FormLoginVue from "./components/FormLogin.vue";
  import ResultFormVue from "./components/ResultForm.vue";
  
  const validado = ref(false);
  const resultado = ref(null);
  
  const elementForms = reactive({
    nome: "",
    idade: "",
    email: "",
    senha: "",
    confirmarSenha: "",
    endereco: "",
    cidade: "",
    hobbie: "",
    linguagens: "",
    biografia: "",
    estadoSelecionado: "",
  });
  
  function validarFormulario(formulario) {
    if (formulario.nome.length < 3 || formulario.nome.length > 20) {
      alert("O nome deve ter entre 3 e 20 caracteres.");
      return false;
    }
    if (new Date().getFullYear() - new Date(formulario.idade).getFullYear() < 18) {
      alert("A idade deve ser maior que 18 anos.");
      return false;
    }
    if (!formulario.email.includes("@")) {
      alert("O e-mail deve ser válido.");
      return false;
    }
    if (formulario.senha !== formulario.confirmarSenha) {
      alert("As senhas não conferem.");
      return false;
    }
    if (formulario.endereco === "") {
      alert("O endereço é obrigatório.");
      return false;
    }
    if (formulario.cidade === "") {
      alert("A cidade é obrigatória.");
      return false;
    }
    if (formulario.estadoSelecionado === "") {
      alert("Selecione um estado.");
      return false;
    }
    if (formulario.hobbie === "") {
      alert("Adicione algum hobbie.");
      return false;
    }
    if (formulario.linguagens === "") {
      alert("Linguagem preferida é obrigatória.");
      return false;
    }
    if (formulario.biografia === "") {
      alert("Biografia é obrigatória.");
      return false;
    }
    resultado.value = { ...formulario };
    validado.value = true;
  }
  </script>
  
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
  