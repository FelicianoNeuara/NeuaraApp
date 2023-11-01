<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="List"
          @click="toggleLeftDrawer"
        />
        
        <div class="q-px-lg q-pt-xl q-mb-md">
        <h2>Minhas Tarefas</h2>
          <div class="text-h6">{{ dataFormatada }}</div>
          <q-img src="src/img/wallpaper.jpg" class="header-image absolute-top"></q-img>
        </div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="drawer"
      show-if-above
      :width="300"
      :breakpoint="600"
      @hide="drawer = false"
    >
      <q-scroll-area style="height: calc(100% - 192px); margin-top: 130px; border-right: 1px solid #ddd">
        <q-list padding>
          <q-item
            to="/"
            exact
            clickable
            v-ripple
          >
            <q-item-section avatar>
              <q-icon name="list" />
            </q-item-section>
            <q-item-section>
             Menu
            </q-item-section>
          </q-item>
          <q-item
            to="/help"
            exact
            clickable
            v-ripple
          >
            <q-item-section avatar>
              <q-icon name="help" />
            </q-item-section>
            <q-item-section>
              Ajuda
            </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>
      <q-img class="absolute-top" src="src/img/wallpaper.jpg" style="height: 135px">
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="56px" class="q-mb-sm">
            <img src="src/img/perfil.jpg">
          </q-avatar>
          <div class="text-weight-bold">Neuara</div>
          <div>felicianoneuara22@gmail.com</div>
        </div>
      </q-img>
    </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view></router-view>
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import { ref } from 'vue';

export default {
  data() {
    return {
      dataFormatada: '',
      drawer: false,
    };
  },
  mounted() {
    this.atualizarData();
  },
  methods: {
    toggleLeftDrawer() {
      this.drawer = !this.drawer;
    },
    atualizarData() {
      const hoje = new Date();
      const options = {
        weekday: 'long',
        year: 'numeric',
        month: 'long',
        day: 'numeric',
        hour: 'numeric',
        minute: 'numeric',
        second: 'numeric',
      };
      this.dataFormatada = hoje.toLocaleDateString('pt-BR', options);
      setTimeout(this.atualizarData, 1000); // Atualiza a cada segundo
    },
  },
};
</script>

<style lang="scss">
.header-image {
  height: 100%;
  z-index: -1;
  opacity: 0.8;
}
</style>
