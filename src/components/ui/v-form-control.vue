<template>
  <div class="inputs">
    <slot name="inputs"></slot>
  </div>
  <div class="actions">
    <slot name="actions"></slot>
  </div>
</template>

<style scoped>
.inputs {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  column-gap: 1.5rem;
  row-gap: 1.5rem;
  padding: 1rem 0rem;
}

.actions {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  padding-top: 1rem;
}
</style>
