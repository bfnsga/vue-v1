<template>
  <div
    :class="{ 'col-span-1': colSpan === '1', 'col-span-2': colSpan === '2' }"
  >
    <label v-if="label" :for="id">{{ label }}</label>
    <input :type="type" :id="id" :name="id" :placeholder="placeholder" />
  </div>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      required: false,
    },
    colSpan: {
      type: String,
      required: false,
      default: "1",
    },
    type: {
      type: String,
      required: true,
      default: "text",
    },
    id: {
      type: String,
      required: false,
    },
    placeholder: {
      type: String,
      required: false,
      default: "",
    },
  },
  computed: {
    inputColumnSpan() {
      if (colSpan === 1) {
        return { "col-span-1": colSpan === 1 };
      } else {
        return { "col-span-2": colSpan === 2 };
      }
    },
  },
};
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
