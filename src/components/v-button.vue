<template>
  <button :class="computedClasses" :disabled="disabled">
    <span class="content" :class="{ invisible: loading }">
      <slot> Default Button </slot>
    </span>
    <div v-if="loading">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="spinner"
        width="100px"
        height="100px"
        viewBox="0 0 100 100"
        preserveAspectRatio="xMidYMid"
      >
        <circle
          cx="50"
          cy="50"
          r="32"
          stroke-width="8"
          stroke="currentColor"
          stroke-dasharray="50.26548245743669 50.26548245743669"
          fill="none"
          stroke-linecap="round"
        >
          <animateTransform
            attributeName="transform"
            type="rotate"
            repeatCount="indefinite"
            dur="1.5s"
            keyTimes="0;1"
            values="0 50 50;360 50 50"
          ></animateTransform>
        </circle>
      </svg>
    </div>
  </button>
</template>

<script>
export default {
  props: {
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
  font-weight: 500;
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
  color: #1e293b;
}

.secondary:hover,
.secondary:active {
  background-color: #f8fafc;
  border-color: #f8fafc;
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
.spinner {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
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
