<template>
  <div class="flex-strip c-check" 
    @click="check" 
    :disabled="disabled" 
    :checked="checked">
    <svg version="1.1" xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 80 80" class="c-check-button">
      <rect x="18" y="18" width="44" height="44" rx="12"  
        stroke="var(--color-border)" stroke-width="4"
        fill="var(--color-back)"/>
      <g v-if="checked">
        <rect x="56" y="15" width="10" height="24"
           stroke-width="0" 
           fill="var(--color-back)" />
        <path d="M 28 37 L 40 50 L 62 26"
          stroke="var(--color-center)" stroke-width="8" 
          stroke-linecap="round" stroke-linejoin="round" 
          fill="none" />
      </g>
    </svg>
    <span class="c-check-label">
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
      if (this.disabled) return
      this.$emit("check")
    }
  }
}
</script>

<style scoped>
.c-check {
  cursor: default;
  --color-border: var(--color-fore);
  --color-center: var(--color-accent);
}

.c-check[disabled="true"] {
  --color-border: var(--color-gray);
  --color-center: var(--color-gray); 
}

.c-check[checked="true"] {

}

.c-check-button {
  height: 1.6rem;
  margin-right: 1rem;
}

.c-check-label {

}
</style>