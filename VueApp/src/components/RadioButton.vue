<template>
  <div class="flex-strip c-radio" 
    @click="check" 
    :disabled="disabled" 
    :checked="checked">
    <svg version="1.1" xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 80 80" class="c-radio-button">
      <circle cx="40" cy="40" r="22"
        fill="var(--color-back)" stroke-width="4" stroke="var(--color-border)" />
      <circle v-if="checked" cx="40" cy="40" r="12" 
        stroke-width="0" fill="var(--color-center)" />
    </svg>
    <span class="c-radio-label">
      <template v-if="text">{{text}}</template>
      <slot v-else></slot>
    </span>
  </div>
</template>

<script>
export default {
  props: {
    text: [String, Number],
    disabled: Boolean,
    checked: Boolean,
    value: undefined
  },
  methods: {
    check () {
      if (this.disabled || this.checked) return
      this.$emit("check")
    }
  }
}
</script>

<style scoped>
.c-radio {
  cursor: default;
  --color-border: var(--color-fore);
  --color-center: var(--color-accent);
}

.c-radio[disabled="true"] {
  --color-border: var(--color-gray);
  --color-center: var(--color-gray); 
}

.c-radio[checked="true"] {
  
}

.c-radio-button {
  height: 1.6rem;
  margin-right: 1rem;
}

.c-radio-label {

}
</style>