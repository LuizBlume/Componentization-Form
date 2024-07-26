<script setup>
import { ref, reactive, watch } from "vue";

const props = defineProps({
  produto: {
    type: Object,
    required: true
  }
});

const estados = ref([
  "AC", "AL", "AP", "AM", "BA", "CE", "DF", "ES", "GO", "MA", "MT", "MS", "MG",
  "PA", "PB", "PR", "PE", "PI", "RJ", "RN", "RS", "RO", "RR", "SC", "SP", "SE", "TO",
]);

const validarLocal = reactive({ ...props.produto });

watch(() => props.produto, (newValue) => {
  Object.assign(validarLocal, newValue);
});

const emit = defineEmits(['validarFormulario']);

function validarFormulario() {
  emit("validarFormulario", validarLocal);
}
</script>

<template>
  <div class="form">
    <div class="borda-form">
      <div class="div-esquerda">
        <h1>Formulário de Cadastro</h1>
        <div class="button-enviar">
          <button @click.prevent="validarFormulario">Enviar</button>
        </div>
      </div>
      <div class="forms">
        <form @submit.prevent="validarFormulario">
          <legend>
            <h2>Dados pessoais</h2>
          </legend>
          <label for="nome">Nome:</label>
          <input type="text" id="nome" v-model.lazy="validarLocal.nome" />
          <label for="data_nasc">Data de nascimento:</label>
          <input type="date" id="data_nasc" v-model.lazy="validarLocal.idade" />
          <label for="email">E-mail:</label>
          <input type="email" id="email" v-model.lazy="validarLocal.email" />
          <label for="password">Senha:</label>
          <input type="password" id="password" v-model.lazy="validarLocal.senha" />
          <label for="confirmarSenha">Confirmar Senha:</label>
          <input type="password" id="confirmarSenha" v-model.lazy="validarLocal.confirmarSenha" />
        </form>
      </div>
      <div class="forms">
        <form>
          <legend>
            <h2>Endereço</h2>
          </legend>
          <label for="endereco">Endereço</label>
          <input type="text" id="endereco" v-model.lazy="validarLocal.endereco" />
          <label for="cidade">Cidade</label>
          <input type="text" id="cidade" v-model.lazy="validarLocal.cidade" />
          <label for="estados">Estado</label>
          <select name="estados" id="estados" v-model.lazy="validarLocal.estadoSelecionado">
            <option value="" disabled selected>Selecione um estado</option>
            <option v-for="(item, index) in estados" :key="index">{{ item }}</option>
          </select>
        </form>
      </div>
      <div class="forms">
        <form>
          <legend>
            <h2>Diversos</h2>
          </legend>
          <label for="hobbies">Hobbies</label>
          <input type="text" id="hobbie" v-model.lazy="validarLocal.hobbie" />
          <label for="linguagens">Linguagens de Programação</label>
          <input type="text" id="linguagens" v-model.lazy="validarLocal.linguagens" />
          <label for="biografia">Biografia</label>
          <textarea id="biografia" v-model.lazy="validarLocal.biografia"></textarea>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import "./sass/style.css";
</style>
