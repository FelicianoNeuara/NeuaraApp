<template>
  <q-page class="q-pa-lg">
    <h5 class="q-mt-none">Preencha os campos </h5>
    <form @submit.prevent="enviarAjuda">
      <q-input
        label="Nome"
        v-model="nome"
      />
      <q-input
        label="Contato"
        v-model="contato"
      />
      <q-input
        label="Email"
        v-model="email"
        type="email"
      />
      <q-input
        label="Assunto"
        v-model="Assunto"
      />
      <q-input
        label="Mensagem de Ajuda"
        v-model="mensagem"
        type="textarea"
      />
      <q-btn
        color="primary"
        label="Enviar Ajuda"
        type="submit"
      />
    </form>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'AjudaPage',
  data() {
    return {
      nome: '',
      contato: '',
      email: '',
      localizacao: '',
      mensagem: ''
    };
  },
  methods: {
    enviarAjuda() {
      // Aqui você pode adicionar lógica para enviar as informações do formulário,
      // por exemplo, fazendo uma chamada para um servidor ou processando os dados localmente.
      // Após o envio, você pode redirecionar o usuário para a página de confirmação ou ação apropriada.
    }
  }
})
</script>