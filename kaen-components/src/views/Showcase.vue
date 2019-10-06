<template>
  <div class="container-fluid">
    <h1 class="display-3">Showcase for {{Comp}}</h1>
    <component v-bind:is="Comp"></component>
  </div>
</template>

<script>

import Components from '../Collection.ts'

export default {
  name: 'ComponentTester',
  components: Components,
  props: {
    
  },
  mounted: function() {
  },
  computed: {
    Comp: function(){return this.$route.params['name'];}
  },
  watch:{

  },
}
</script>

<style scoped>

</style>
