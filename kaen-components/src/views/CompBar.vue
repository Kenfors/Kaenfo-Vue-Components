<template>
  <div class="container-fluid p-0">
      <div class="list-group-item">
          <div v-on:click="FontActive=!FontActive">
            Fonts
          </div>
          <div v-if="FontActive">
            <div v-for="font in Fonts" v-bind:key="font"
            v-on:click="route(font)"
            class="list-group-item border-0">
                {{font}}
            </div>

          </div>
      </div>
      <div class="list-group-item">Other</div>
      <div class="list-group-item">Other</div>
      <div class="list-group-item">Other</div>
  </div>
</template>

<script>

import Components from '../Collection.ts'

export default {
  name: 'CompNav',
  components: Components,
  data: function(){return {
        Fonts: [],
        FontActive: false,


      }
  },
  props: {
    
  },
  methods:{
      route: function(route){
          this.$root.$router.push({name:'showcase', params: {name: route}});
      },
  },
  mounted: function() {
      

    for (var comp in Components){
        console.log("Compoenent: " + comp);
        if(comp.includes('font')){
            this.Fonts.push(comp);
            continue;
        }
    }

  },
  computed: {


  },
  watch:{

  },
}
</script>

<style scoped>

</style>