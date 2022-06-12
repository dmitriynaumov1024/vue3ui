<template>
  <div class="app-container pad-8px">
    <div class="margin-bottom">
      <h1 class="margin-bottom">This is vue3ui</h1>
      <p>&ndash; my attempt of creating UI library for <b>Vue 3</b>.</p>
    </div>
    <div class="card margin-bottom-2">
      <RbShowcase />
    </div>
    <div class="card margin-bottom-2">
      <CbShowcase />
    </div>
    <div class="card margin-bottom-2">
      <TbShowcase />
    </div>
  </div>
</template>

<script>
import RbShowcase from "./compshowcase/RbShowcase.vue"
import CbShowcase from "./compshowcase/CbShowcase.vue"
import TbShowcase from "./compshowcase/TbShowcase.vue"

export default {
  components: {
    RbShowcase,
    CbShowcase,
    TbShowcase
  }
}
</script>

<style>

</style>
