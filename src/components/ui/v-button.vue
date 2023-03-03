<template>
  <button :class="computedClasses" :disabled="disabled">
    <span class="content" :class="{ invisible: loading }">
      {{ content }}
    </span>
    <div v-if="loading">
      <v-icon-spinner></v-icon-spinner>
    </div>
  </button>
</template>

<script>
import VIconSpinner from "../icons/v-icon-spinner.vue";

export default {
  components: {
    VIconSpinner,
  },
  props: {
    content: {
      type: String,
      required: true,
      default: "Default Button",
    },
    type: {
      type: String,
      default: "primary",
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    loading: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    computedClasses() {
      const classArray = [];

      if (this.disabled) {
        classArray.push("disabled");
      }

      classArray.push(this.type);
      return classArray;
    },
  },
};
</script>

<style scoped>
button {
  position: relative;
  padding: 0.575rem 2rem;
  border-radius: 0.06125rem;
  font-family: inherit;
  font-weight: 600;
  font-size: 1.06125rem;
  border: 1px solid;
  color: white;
  cursor: pointer;
}

/*****************************/
/* Color */
/*****************************/

/* Primary */
.primary {
  background-color: #3399ff;
  border-color: #3399ff;
  color: white;
}

.primary:hover,
.primary:active {
  background-color: #0a85ff;
  border-color: #0a85ff;
}

/* Danger */
.danger {
  background-color: #dc3545;
  border-color: #dc3545;
  color: white;
}

.danger:hover,
.danger:active {
  background-color: #d02536;
  border-color: #d02536;
}

/* Secondary */
.secondary {
  background-color: #ffffff;
  border-color: #ffffff;
  color: #cbd5e1;
}

.secondary:hover,
.secondary:active {
  background-color: #f8fafc;
  border-color: #f8fafc;
  color: #94a3b8;
}

svg {
  background-color: transparent;
  height: 1.375rem;
  width: 1.375rem;
}

.disabled {
  opacity: 0.6;
}

.content {
  position: relative;
  display: flex;
  align-items: center;
  line-height: normal;
}
.invisible {
  visibility: hidden;
}

.flat {
  background-color: transparent;
  color: #3a0061;
  border: none;
}

.flat:hover,
.flat:active {
  background-color: #edd2ff;
}
</style>
