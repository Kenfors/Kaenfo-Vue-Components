<template>
  <div id="app" class="container-fluid p-0">
    <div class="list-group-item">
      <router-link to="/">Home</router-link>
    </div>
    <div class="container-fluid row p-0">
      <aside class="col-2 p-0">
        <comp-bar></comp-bar>
      </aside>
      <main class="col-8 p-0">
        <router-view/>

      </main>
    </div>


  </div>
</template>

<script>
import CompBar from './views/CompBar'

export default {
  name: 'App',
  components: {
    CompBar,

  }
  
}
</script>

<style>


</style>
