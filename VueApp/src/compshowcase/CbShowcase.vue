<template>
  <div>
    <h2 class="margin-bottom">Check button showcase</h2>
    <CheckButtonList :items="items"
      v-model:indexes="selectedIndexes"
      class="margin-bottom"/>
    <template v-if="selectedItems">
      <p>Selected items: {{selectedItems}}</p>
    </template>
  </div>
</template>

<script>
import CheckButtonList from "../components/CheckButtonList.vue"

export default {
  components: {
    CheckButtonList
  },
  data () {
    return {
      items: [
        { text: "Ford" },
        { text: "Dodge" },
        { text: "Buick", disabled: true },
        { text: "Chevrolet" }
      ],
      selectedIndexes: []
    }
  }, 
  computed: {
    selectedItems () {
      if (this.selectedIndexes.length)
        return this.selectedIndexes
          .map(index => this.items[index].text)
          .join(", ")
      else
        return undefined
    }
  }
}
</script>
