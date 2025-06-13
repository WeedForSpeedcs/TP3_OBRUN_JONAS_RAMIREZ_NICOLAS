<template>
  <button :class="['base-button', `base-button--${color}`]" :disabled="disabled">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'BaseButton',
  props: {
    disabled: {
      type: Boolean,
      default: false,
    },
    color: {
      type: String,
      default: 'primary',
      validator: (value) => ['primary', 'warn', 'danger'].includes(value),
    },
  },
}
</script>

<style scoped>
.base-button {
  background-color: #42b983; 
  color: white;
  padding: 0.8rem 1.5rem;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

.base-button:hover:not([disabled]) {
  background-color: #369b71; 
  transform: translateY(-2px);
}

.base-button:focus:not([disabled]) {
  outline: none;
  box-shadow: 0 0 0 3px rgba(66, 185, 131, 0.5); 
}


.base-button--warn {
  background-color: #ff5722; 
}

.base-button--warn:hover:not([disabled]) {
  background-color: #e64a19; 
}

.base-button--warn:focus:not([disabled]) {
  box-shadow: 0 0 0 3px rgba(255, 87, 34, 0.5); /* Orange focus shadow */
}


.base-button--danger {
  background-color: #ef5350; 
}

.base-button--danger:hover:not([disabled]) {
  background-color: #d32f2f; 
}

.base-button--danger:focus:not([disabled]) {
  box-shadow: 0 0 0 3px rgba(239, 83, 80, 0.5); 
}

.base-button[disabled] {
  background-color: #cccccc;
  cursor: not-allowed;
  opacity: 0.7;
}
</style> 