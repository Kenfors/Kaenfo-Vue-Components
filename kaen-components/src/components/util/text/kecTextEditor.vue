<template>
  <div>
    <div v-if="showTools" v-bind:style="toolStyle">
      <button 
      v-for="(butt, index) in buttons" v-bind:key="index"
      v-on:click="buttonClick(butt.cmd, butt.val)"
      ><i class="material-icons md-36">{{butt.icon}}</i></button>
    </div>
    <div v-else v-bind:style="toolStyle"></div>
    <div 
    v-on:click="showTools=true"
    class="kecTextEditorBox"
    contenteditable="true" v-bind:style="boxstyle">

    </div>
  </div>
</template>

<script>

export default {
  name: 'util-texteditor',
  props: {
    setTitle : String,
  },
  data: function(){
    return {
      title: 'TextEditor',
      showTools: false,

      buttons: [
        {cmd: 'none', val: 'none', icon: 'format_size'},
        {cmd: 'formatBlock', val: 'p', icon: 'text_fields'},
        {cmd: 'formatBlock', val: 'h1', icon: 'title'},
        {cmd: 'insertUnorderedList', val: 'none', icon: 'format_list_bulleted'},
        {cmd: 'insertOrderedList', val: 'none', icon: 'format_list_numbered'},
        {cmd: 'justifyLeft', val: 'none', icon: 'format_align_left'},
        {cmd: 'justifyCenter', val: 'none', icon: 'format_align_center'},
        {cmd: 'justifyRight', val: 'none', icon: 'format_align_right'},
        {cmd: 'bold', val: 'none', icon: 'format_bold'},
        {cmd: 'italic', val: 'none', icon: 'format_italic'},
        {cmd: 'underline', val: 'none', icon: 'format_underlined'},

      ],



      boxstyle: {
        minHeight: '100px',
        border: '1px solid darkgray',
        outline: 'none',
        padding: '10px'

      },
      toolStyle: {
        height: "40px",
      },

    }
  },
  mounted: function(){
    this.initOutsideClick();
  },
  methods: {
    initOutsideClick: function() {
      let vm = this;
      window.addEventListener('click', function(e){   
        if (!vm.$el.contains(e.target)){
          vm.showTools = false;
        }
      });
    },
    buttonClick: function(cmd, val){
      let textBox = this.$el.getElementsByClassName("kecTextEditorBox")[0];

      // Handle commands
      document.execCommand(cmd,false,val);


      textBox.focus();
    },
  }

}
</script>

<style scoped>
button {
  display: inline-block;
  background-color: lightgray;
  border: none;
  margin: 1px;
  outline: none;

}
button:hover {
  opacity: 0.5;
  
}

</style>
