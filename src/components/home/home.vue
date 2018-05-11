<template>
  <div class="grid">
    <!--<Card dis-hover v-for="item in mag" :key="item" class="grid-item grid-item&#45;&#45;width2">-->
      <!--<div style="text-align:center">-->
        <!--<img style="width: 100%" :src=item>-->
        <!--<h3>アナスタシア</h3>-->
      <!--</div>-->
    <!--</Card>-->
    <Card dis-hover class="grid-item grid-item--width2">
      <div style="text-align:center">
        <img style="width: 100%" src="./1.jpg">
        <h3>アナスタシア</h3>
      </div>
    </Card>
    <Card dis-hover class="grid-item grid-item--width2">
      <div style="text-align:center">
        <img style="width: 100%" src="./1.jpg">
        <h3>アナスタシア</h3>
      </div>
    </Card>
  </div>
</template>

<script>
import axios from 'axios'
import '../../assets/plugin/wookmark/wookmark'
export default {
  name: 'home',
  data () {
    return {
      mag: ''
    }
  },
  methods: {
    init: async () => {
    }
  },
  mounted () {
    // this.init()
    let wookmark = new Wookmark('.grid')
  },
  async created () {
    try {
      let {data, status} = await axios({
        method: 'post',
        url: 'http://localhost:3000/p1'
      })
      if (status === 200) {
        // this.mag = data
      }
    } catch (e) {
      console.log(e);
    }
  },
  components: {
  },
  updated () {
  }
}
</script>

<style scoped>
  @import "./home.css";
  @import "../../assets/plugin/wookmark/main.css";
</style>
