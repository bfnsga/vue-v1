<template>
	<VButton content="Open Modal" @click="createAlbumModal = !createAlbumModal" />
	<HelloWorld msg="Vite + Vue" />
	<v-modal v-if="createAlbumModal" title="Create Album" @close="createAlbumModal = !createAlbumModal">
		<template #section>
			<p>
				Are you sure you want to delete these 2 items?
			</p>
			<v-form-control>
				<template #inputs>
					<v-input type="text" span="1"></v-input>
				</template>
			</v-form-control>
		</template>
		<template #actions>
			<VButton content="Create" />
		</template>
	</v-modal>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import HelloWorld from "./components/HelloWorld.vue";
import VButton from "./components/ui/v-button.vue";
import VModal from "./components/ui/v-modal.vue";
import VInput from "./components/ui/v-input.vue";
import VFormControl from "./components/ui/v-form-control.vue";

export default defineComponent({
	components: {
		HelloWorld,
		VButton,
		VModal,
		VInput,
		VFormControl
	},
	data() {
		return {
			createAlbumModal: false
		};
	}
})
</script>

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

/* we will explain what these classes do next! */
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

</style>
