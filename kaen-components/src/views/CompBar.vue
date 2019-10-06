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
      <div class="list-group-item">
          <div v-on:click="MediaActive=!MediaActive">
            Media
          </div>
          <div v-if="MediaActive">
            <div v-for="med in Media" v-bind:key="med"
            v-on:click="route(med)"
            class="list-group-item border-0">
                {{med}}
            </div>

          </div>
      </div>
      <div class="list-group-item">
          <div v-on:click="UtilityActive=!UtilityActive">
            Utilities
          </div>
          <div v-if="UtilityActive">
            <div v-for="util in Utilities" v-bind:key="util"
            v-on:click="route(util)"
            class="list-group-item border-0">
                {{util}}
            </div>
          </div>
      </div>


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

        Media: [],
        MediaActive: false,

        Utilities: [],
        UtilityActive: false,

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
        if(comp.includes('font')){
            this.Fonts.push(comp);
            continue;
        }
        if(comp.includes('media')){
            this.Media.push(comp);
            continue;
        }
        if(comp.includes('util')){
            this.Utilities.push(comp);
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