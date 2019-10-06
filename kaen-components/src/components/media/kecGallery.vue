<template>
  <div class="row">
    <div class="d-flex flex-column align-content-center p-0"
    v-bind:class="colsize"
    v-for="colIndx in Columns" v-bind:key="colIndx"
    >
      <div class="p-1 d-flex justify-content-center kec-image-container"
        v-for="(pic, index) in pics(colIndx)" v-bind:key="index"
      >
        <img v-bind:src="pic" alt="No Image." class="kec-image mx-auto d-block">
      </div>

    </div>
    <div style="margin-top:500px;">Gallery</div>
  </div>
</template>

<script>

export default {
  name: 'media-gallery',
  props: {
    Images: Array,
    InCols: Number,
  },
  data: () => {
    return {
      Columns: 3,
      pictures: [
        'https://via.placeholder.com/700x300',
        'https://via.placeholder.com/300x400',
        'https://via.placeholder.com/700x600',
        'https://via.placeholder.com/500x500', 
        'https://via.placeholder.com/200x250',
        'https://via.placeholder.com/100x120',
        'https://via.placeholder.com/150x440',
        'https://via.placeholder.com/230x222',
        'https://via.placeholder.com/700x650',
        'https://via.placeholder.com/450x100',
        'https://via.placeholder.com/250x550',
        'https://via.placeholder.com/120x700',
        ]
    }

  },
  mounted: function(){
    //Setup props.

  },
  computed: {
      colsize: function(){
        
        switch(this.Columns){
          case 1:
            return {'col-12': true}
          break;
          case 2:
            return {'col-6': true}
          break;
          case 3:
            return {'col-4': true}
          break;
          case 4:
            return {'col-3': true}
          break;
          default:
            return {'col-12': true}
          break;

        }

      },
    
    },
  methods: {
    pics: function(col){
      let list = [];
      console.log("Listing col..." + col);
      for(let i = col-1; i < this.pictures.length;i+=this.Columns){
        console.log("Pushing: " + i);
        list.push(this.pictures[i]);
      }
      return list;
    },
    
  },

}
</script>

<style scoped>

.kec-image {
  min-width: 100%;
  height: auto;
  object-fit: cover;

  transform: scale(1);
  opacity: 0.5;
  box-shadow: none;
  transition: opacity 0.3s, min-width 0.3s, transform 0.3s, box-shadow 0.3s;

}
.kec-image:hover {
  position: relative;
  z-index: 1000;

  box-shadow: 0 0 4px 2px gray;
  transform: scale(1.1);
  opacity: 1;
}

.kec-image-container {
  max-height: 80vh;
  
}

</style>
