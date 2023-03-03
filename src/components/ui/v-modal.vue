<template>
  <div @click="$emit('close')"></div>
  <dialog open>
    <header>
      <h2>{{ title }}</h2>
      <button type="button" @click="$emit('close')">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="24"
          height="24"
          viewBox="0 0 24 24"
          stroke-width="2"
          stroke="currentColor"
          fill="none"
          stroke-linecap="round"
          stroke-linejoin="round"
        >
          <path stroke="none" d="M0 0h24v24H0z" fill="none"></path>
          <path d="M18 6l-12 12"></path>
          <path d="M6 6l12 12"></path>
        </svg>
      </button>
    </header>
    <section>
      <slot name="section"></slot>
    </section>
    <menu>
      <slot name="actions"> </slot>
    </menu>
  </dialog>
</template>

<script>
import VButton from "./v-button.vue";
export default {
  components: {
    VButton,
  },
  props: ["title"],
  emits: ["close"],
};
</script>

<style scoped>
div {
  position: fixed;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100%;
  background-color: rgba(0, 0, 0, 0.4);
  z-index: 10;
}

dialog {
  position: fixed;
  top: 20vh;
  left: 10%;
  width: 80%;
  z-index: 100;
  border-radius: 2px;
  border: none;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 0;
  margin: 0;
  overflow: hidden;
}

header {
  background-color: #f1f5f9;
  color: #1e293b;
  padding: 0.75rem 1.5rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

header h2 {
  margin: 0;
  font-weight: 800;
  font-size: 1.35rem;
}

header button {
  padding: 0rem;
  background-color: transparent;
  border: none;
}

header button svg {
  color: #94a3b8;
  margin-top: 0.5rem;
  width: 1.25rem;
  height: 1.25rem;
}

header button svg:hover {
  color: #475569;
}

section {
  padding: 0.5rem 1.5rem;
}

section p {
  color: #1e293b;
  font-size: 1.1rem;
  text-align: left;
  line-height: 1.75rem;
}

menu {
  padding: 1.25rem 1.5rem;
  display: flex;
  justify-content: flex-end;
  margin: 0;
}

@media (min-width: 768px) {
  dialog {
    left: calc(50% - 17rem);
    width: 34rem;
  }
}
</style>
