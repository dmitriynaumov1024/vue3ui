<template>
  <div>
    <div v-for="(item, i) in items" :key="i" class="list-item-wrap">
      <CheckButton :text="item.text" 
        :checked="isChecked(i)" 
        :disabled="isDisabled(item)" 
        @check="() => check(i)" />
    </div>
  </div>
</template>

<script>
import CheckButton from "./CheckButton.vue"

export default {
  components: {
    CheckButton
  },
  props: {
    indexes: Object,
    items: Object
  },
  methods: {
    isDisabled (item) {
      return item.disabled == true
    },
    isChecked (index) {
      return this.indexes.find(item => item == index) != undefined
    },
    check (index) {
      var newIndexes = this.isChecked(index) ?
        this.indexes.filter(i => i != index) :
        this.indexes.concat(index).sort((a, b) => a - b)
      this.$emit("update:indexes", newIndexes)
    }
  }
}
</script>