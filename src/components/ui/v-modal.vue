<template>
	<transition name="fade" appear>
		<div class="background"></div>
	</transition>
	<Transition>
		<dialog open>
			<header>
				<h2>{{ title }}</h2>
				<button type="button" @click="$emit('close')">
					<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round">
						<path stroke="none" d="M0 0h24v24H0z" fill="none"></path>
						<path d="M18 6l-12 12"></path>
						<path d="M6 6l12 12"></path>
					</svg>
				</button>
			</header>
			<div class="section">
				<div>
					<slot name="section"></slot>
				</div>
				<div class="menu">
					<slot name="actions"></slot>
				</div>
			</div>
		</dialog>
	</Transition>
</template>

<script>
import VButton from "./v-button.vue";
export default {
	components: {
		VButton,
	},
	props: ["title"],
	emits: ["close"]
};
</script>

<style scoped>
.background {
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
  top: 15vh;
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
  margin-top: 0.4rem;
  width: 1.25rem;
  height: 1.25rem;
}

header button svg:hover {
  color: #475569;
}

.section {
  padding: 1rem 2rem 1.75rem 2rem;
}

p {
  color: #1e293b;
  font-size: 1.1rem;
  text-align: left;
  line-height: 2rem;
  text-align: left;
}

.menu {
  display: flex;
  justify-content: flex-start;
  padding-top: 0.875rem;
}

@media (min-width: 768px) {
  dialog {
    left: calc(50% - 17rem);
    width: 34rem;
  }
}

.hidden {
  display: none;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
