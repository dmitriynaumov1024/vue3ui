<template>
  <div>
    <div v-for="(item, i) in items" :key="i" class="list-item-wrap">
      <RadioButton :text="item.text" 
        :checked="isChecked(i)" 
        :disabled="isDisabled(item)" 
        @check="() => check(i)" />
    </div>
  </div>
</template>

<script>
import RadioButton from "./RadioButton.vue"

export default {
  components: {
    RadioButton
  },
  props: {
    modelValue: Object,
    index: Number,
    items: Object
  },
  methods: {
    isDisabled (item) {
      return item.disabled == true
    },
    isChecked (index) {
      return this.index == index || this.items[index] == this.modelValue
    },
    check (index) {
      this.$emit("update:index", index)
      this.$emit("update:modelValue", this.items[index])
    }
  }
}
</script>