<template>
  <div id="app">
    <p>
      A Vue.js component to draw animated circular progress bars!
    </p>
      <vue-circle
        ref="myprogress"
        id="circle"
        :progress="p"
        :size="100"
        :reverse="false"
        line-cap="round"
        :fill="fill"
        empty-fill="rgba(0, 0, 0, .1)"
        :animation-start-value="0.0"
        :start-angle="0"
        insert-mode="append"
        :thickness="5"
        :show-percent="true"
        @vue-circle-progress="progress"
        @vue-circle-end="progress_end"
        >
      </vue-circle>
      <button @click="redraw">Redraw</button>
  </div>
</template>

<script>
  import VueCircle from '../src/index.vue'
  export default {
    components: {
      VueCircle
    },
    data(){
      return{
        fill : { gradient: ["red", "green", "blue"] },
        p:10
      }
    },
    methods:{
      progress(event,progress,stepValue){
        console.log(stepValue);
      },
      progress_end(event){
        console.log("Circle progress end");
      },
      redraw(){
        this.$refs.myprogress.updateProgress(60);
      }
    }
  }
</script>

<style scoped>
  @import 'https://fonts.googleapis.com/css?family=Ruda';
</style>
