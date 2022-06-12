<template>
  <div>
    <h2 class="margin-bottom">Toggle button showcase</h2>
    <div class="list-item-wrap">
      <ToggleButton v-model="item1">
        Want to activate <i>this</i> ?
      </ToggleButton>
    </div>
    <div class="list-item-wrap">
      <ToggleButton v-model="item2">
        Or maybe <i><u>this</u></i> ?
      </ToggleButton>
    </div>
    <div class="list-item-wrap">
      <ToggleButton v-model="item3" :disabled="true">
        This one is always active
      </ToggleButton>
    </div>
  </div>
</template>

<script>
import ToggleButton from "../components/ToggleButton.vue"

export default {
  components: {
    ToggleButton
  },
  data () {
    return {
      item1: false,
      item2: true,
      item3: true
    }
  }
}
</script>
