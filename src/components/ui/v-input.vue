<template>
  <div :class="inputSpan">
    <label v-if="label" :for="id">{{ label }}</label>
    <input :type="type" :id="id" :name="id" :placeholder="placeholder" />
  </div>
</template>

<script setup lang='ts'>
import { computed } from 'vue';

interface Props {
  type: string,
  label?: string,
  span?: string,
  id?: string,
  placeholder?: string
}

const props = withDefaults(defineProps<Props>(), {
  type: 'text',
  span: '2'
});

const inputSpan = computed(() => {
  if (props.span === '1') {
    return ['col-span-1'];
  }
});

</script>

<style scoped>
div {
  display: flex;
  flex-direction: column;
}

div .col-span-1 {
  grid-column: span 1 / span 1;
}

div .col-span-2 {
  grid-column: span 2 / span 2;
}

label {
  text-align: left;
  font-weight: 700;
  color: #334155;
  margin-bottom: 0.25rem;
  font-size: 0.95rem;
  letter-spacing: 0.0125rem;
}

input {
  font-size: 1rem;
  font-weight: 400;
  color: #1e293b;
  padding: 0.75rem;
  border: 1.5px solid #e2e8f0;
  border-radius: 2px;
}

input:focus {
  border: 1.5px solid #cbd5e1;
  outline: 2px solid transparent;
  outline-offset: 2px;
}

input::placeholder {
  color: #94a3b8;
}
</style>
