<script setup>
import { reactive } from "vue";

const divResultado = document.getElementById("resultado");

const elementForms = reactive({
  nome: "",
  idade: "",
  email: "",
  senha: "",
  confirmarSenha: "",
  endereco: "",
  cidade: "",
  estados: [
    "AC", "AL", "AP", "AM", "BA", "CE", "DF", "ES", "GO", "MA", "MT", "MS", "MG",
    "PA", "PB", "PR", "PE", "PI", "RJ", "RN", "RS", "RO", "RR", "SC", "SP", "SE", "TO",
  ],
  hobbie: "",
  linguagens: "",
  biografia: "",
  estadoSelecionado: "",
  mostrarMensagem: false,
  mostrarInformacoes: false,
});

const numero = 1;

const mudarMsg = () => {
  elementForms.mostrarMensagem = !elementForms.mostrarMensagem;
};

function validarFormulario() {
  if (elementForms.nome.length < 3 || elementForms.nome.length > 20) {
    alert("O nome deve ter entre 3 e 20 caracteres.");
    return false;
  }
  // if (elementForms.idade < 18) {
  //   alert("A idade deve ser maior que 18 anos.");
  //   return false;
  // }
  // if (!elementForms.email.includes("@")) {
  //   alert("O e-mail deve ser válido.");
  //   return false;
  // }
  // if (elementForms.senha !== elementForms.confirmarSenha) {
  //   alert("As senhas não conferem.");
  //   return false;
  // }
  // if (elementForms.endereco === "") {
  //   alert("O endereço é obrigatório.");
  //   return false;
  // }
  // if (elementForms.cidade === "") {
  //   alert("A cidade é obrigatória.");
  //   return false;
  // }
  // if (elementForms.estadoSelecionado === "") {
  //   alert("Selecione um estado.");
  //   return false;
  // }
  // if (elementForms.hobbie === "") {
  //   alert("Adicione algum hobbie.");
  //   return false;
  // }
  // if (elementForms.linguagens === "") {
  //   alert("Linguagem preferida é obrigatória.");
  //   return false;
  // }
  // if (elementForms.biografia === "") {
  //   alert("Biografia é obrigatória.");
  //   return false;
  // }
  emit("validarFormulario", elementForms)
}
</script>

<template>
  <div class="form">
    <div class="borda-form">
      <div class="div-esquerda">
        <h1>Formulário de Cadastro</h1>
        <div class="button-enviar">
          <button @click="validarFormulario">Enviar</button>
        </div>
      </div>
      <div class="forms">
        <form action="">
          <legend><h2>Dados pessoais</h2></legend>
          <label for="nome">Nome:</label>
          <input type="text" id="nome" v-model.lazy="elementForms.nome" />
          <label for="data_nasc">Data de nascimento:</label>
          <input type="date" id="data_nasc" v-model.number.lazy="elementForms.idade" />
          <label for="email">E-mail:</label>
          <input type="email" id="email" v-model.lazy="elementForms.email" />
          <label for="password">Senha:</label>
          <input type="password" id="password" v-model.lazy="elementForms.senha" />
          <label for="password">Confirmar Senha:</label>
          <input type="password" id="confirmarSenha" v-model.lazy="elementForms.confirmarSenha" />
        </form>
      </div>
      <div class="forms">
        <form action="">
          <legend><h2>Endereço</h2></legend>
          <label for="endereco">Endereço</label>
          <input type="text" id="endereco" v-model.lazy="elementForms.endereco" />
          <label for="cidade">Cidade</label>
          <input type="text" id="cidade" v-model.lazy="elementForms.cidade" />
          <label for="estados">Estado</label>
          <select name="estados" id="estados" v-model.lazy="elementForms.estadoSelecionado">
            <option value="" disabled selected>Selecione um estado</option>
            <option v-for="(item, index) in elementForms.estados" :key="index">
              {{ item }}
            </option>
          </select>
        </form>
      </div>
      <div class="forms">
        <form action="">
          <legend><h2>Diversos</h2></legend>
          <label for="hobbies">Hobbies</label>
          <input type="text" id="hobbie" v-model.lazy="elementForms.hobbie" />
          <label for="linguagens">Linguagens de Programação</label>
          <input type="text" id="linguagens" v-model.lazy="elementForms.linguagens" />
          <label for="biografia">Biografia</label>
          <textarea id="biografia" v-model.lazy="elementForms.biografia"></textarea>
        </form>
      </div>
    </div>
  </div>
  <div class="resultados-area" id="resultado">
    <div class="resultados-content">
      <button v-if="elementForms.mostrarInformacoes" @click="mudarMsg">
        {{ elementForms.mostrarMensagem ? 'Esconder Informações' : 'Mostrar Informações' }}
      </button>
      <div class="resultado" v-if="elementForms.mostrarMensagem">
        <ul>
          <li v-if="elementForms.nome">Nome: <span>{{ elementForms.nome }}</span></li>
          <li v-if="elementForms.idade">Ano de nascimento: <span>{{ elementForms.idade }}</span></li>
          <li v-if="elementForms.email">E-mail: <span>{{ elementForms.email }}</span></li>
          <li v-if="elementForms.senha">Senha: <span>{{ elementForms.senha }}</span></li>
          <li v-if="elementForms.confirmarSenha && elementForms.confirmarSenha === elementForms.senha">
            Confirmação de senha: <span>{{ elementForms.confirmarSenha }}</span>
          </li>
          <li v-if="elementForms.endereco">Endereço: <span>{{ elementForms.endereco }}</span></li>
          <li v-if="elementForms.cidade">Cidade: <span>{{ elementForms.cidade }}</span></li>
          <li v-if="elementForms.estadoSelecionado">Estado: <span>{{ elementForms.estadoSelecionado }}</span></li>
          <li v-if="elementForms.hobbie">Hobbies: <span>{{ elementForms.hobbie }}</span></li>
          <li v-if="elementForms.linguagens">Linguagens de programação: <span>{{ elementForms.linguagens }}</span></li>
          <li v-if="elementForms.biografia">Biografia: <span>{{ elementForms.biografia }}</span></li>
        </ul>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import "./sass/style.css";
</style>
