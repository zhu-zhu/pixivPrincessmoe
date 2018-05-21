<template>
  <div id="main" class="loading">
    <div class="grid">
      <div v-for="item in mag" :key="item" class="grid-item grid-item--width2">
        <img :src=item alt="aa" />
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios'
  import '../../assets/plugin/wookmark/wookmark.js'
  import imagesLoaded from 'imagesloaded'
  import anime from 'animejs'
  export default {
    name: 'home',
    data () {
      return {
        mag: ''
      }
    },
    methods: {

    },
    mounted () {
    },
    async created () {
      try {
        let {data, status} = await axios({
          method: 'post',
          url: 'http://localhost:3000/p1'
        })
        if (status === 200) {
          this.mag = data
        }
      } catch (e) {
        console.log(e);
      }
      this.$nextTick(() => {
        imagesLoaded( document.querySelector('.grid'), () => {
          let wookmark = new Wookmark('.grid');
          document.querySelector('#main').classList.remove('loading')
          let reverseAnim = anime({
            targets: '.grid-item',
            duration: function(t,i) {
              return 500 + i*50;
            },
            easing: 'easeOutExpo',
            delay: function(t,i) {
              return i * 20;
            },
            opacity: {
              value: [0,1],
              duration: function(t,i) {
                return 250 + i*50;
              },
              easing: 'linear'
            },
            translateY: [400,0]
          });
        })
      })
    },
    components: {
    }
  }
</script>

<style scoped>
  @import "./home.css";
  @import "../../assets/plugin/wookmark/main.css";
</style>
