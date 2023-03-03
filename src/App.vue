<script setup lang="ts">
import HelloWorld from "./components/HelloWorld.vue";
import VButton from "./components/ui/v-button.vue";
import VModal from "./components/ui/v-modal.vue";

export default {};
</script>

<template>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <v-button :loading="false">Submit</v-button>
  <HelloWorld msg="Vite + Vue" />
  <v-modal title="Create Album">
    <template #section>
      <p>Testing</p>
    </template>
    <template #actions>
      <VButton content="Cancel" type="secondary" style="margin-right: 10px" />
      <VButton content="Create" />
    </template>
  </v-modal>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
