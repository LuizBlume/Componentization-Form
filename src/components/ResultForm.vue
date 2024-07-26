<template>
    <div class="resultados-area" id="resultado">
      <div class="resultados-content">
        <div class="resultado">
          <ul>
            <li>Nome: <span>{{ resultado.nome }}</span></li>
            <li>Data de nascimento: <span>{{ resultado.idade }}</span></li>
            <li>E-mail: <span>{{ resultado.email }}</span></li>
            <li>Senha: <span>{{ resultado.senha }}</span></li>
            <li>Confirmar Senha: <span>{{ resultado.confirmarSenha }}</span></li>
            <li>Endereço: <span>{{ resultado.endereco }}</span></li>
            <li>Cidade: <span>{{ resultado.cidade }}</span></li>
            <li>Estado: <span>{{ resultado.estadoSelecionado }}</span></li>
            <li>Hobbies: <span>{{ resultado.hobbie }}</span></li>
            <li>Linguagens de Programação: <span>{{ resultado.linguagens }}</span></li>
            <li>Biografia: <span>{{ resultado.biografia }}</span></li>
          </ul>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  const props = defineProps({
    resultado: {
      type: Object,
      required: true
    }
  });
  </script>
  
  <style scoped>
  .resultados-area {
    padding: 20px;
  }
  .resultados-content {
    background-color: #fff;
    border-radius: 8px;
    padding: 20px;
  }
  .resultado ul {
    list-style: none;
    padding: 0;
  }
  .resultado li {
    margin-bottom: 10px;
  }
  </style>
  