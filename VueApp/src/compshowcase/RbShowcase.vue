<template>
  <div>
    <h2 class="margin-bottom">Radio button showcase</h2>
    <RadioButtonList :items="items"
      v-model:index="selectedIndex"
      class="margin-bottom"/>
    <template v-if="selectedItem">
      <p>Selected index: {{selectedIndex}}</p>
      <p>Selected item: {{selectedItem.text}}</p>
    </template>
  </div>
</template>

<script>
import RadioButtonList from "../components/RadioButtonList.vue"

export default {
  components: {
    RadioButtonList
  },
  data () {
    return {
      items: [
        { text: "Item 1" },
        { text: "Item 2" },
        { text: "Item disabled", disabled: true }
      ],
      selectedIndex: undefined
    }
  }, 
  computed: {
    selectedItem () {
      if (typeof (this.selectedIndex) == "number") 
        return this.items[this.selectedIndex]
      else 
        return undefined
    }
  }
}
</script>
