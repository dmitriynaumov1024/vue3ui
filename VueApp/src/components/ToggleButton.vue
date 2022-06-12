<template>
  <div class="flex-strip c-toggle" 
    @click="check" 
    :disabled="disabled" 
    :checked="modelValue">
    <span class="c-toggle-label spacer">
      <template v-if="text">{{text}}</template>
      <slot v-else></slot>
    </span>
    <svg version="1.1" xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 130 80" class="c-toggle-button">
      <rect x="17" y="22" width="96" height="36" rx="18"  
        stroke="var(--color-border)" stroke-width="4"
        fill="var(--color-back)"/>
      <g v-if="modelValue">
        <circle cx="90" cy="40" r="22"
          stroke="var(--color-border)" stroke-width="4"
          fill="var(--color-back)" />
        <circle cx="90" cy="40" r="12" 
          stroke-width="0" fill="var(--color-center)" />
      </g>
      <g v-else>
        <circle cx="40" cy="40" r="22"
          stroke="var(--color-border)" stroke-width="4"
          fill="var(--color-back)" />
      </g>
    </svg>
  </div>
</template>

<script>
export default {
  props: {
    text: String,
    disabled: Boolean,
    modelValue: Boolean
  },
  computed: {
    checked() {
      return this.modelValue
    }
  },
  methods: {
    check () {
      if (this.disabled) return
      this.$emit("update:modelValue", !(this.modelValue))
    }
  }
}
</script>

<style scoped>
.c-toggle {
  cursor: default;
  --color-border: var(--color-fore);
  --color-center: var(--color-accent);
}

.c-toggle[disabled="true"] {
  --color-border: var(--color-gray);
  --color-center: var(--color-gray); 
}

.c-toggle[checked="true"] {

}

.c-toggle-button {
  height: 1.6rem;
  flex-shrink: 0;
}

.c-toggle-label {
  margin-right: 1rem;
}
</style>
