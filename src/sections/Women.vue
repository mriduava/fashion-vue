<template>
 <div class="container-fluid pl-5 pr-5 mxl-md-5 mr-md-5">
   <div class="row">
    <div class="col-lg-3 col-md-4 col-sm-6" v-for="woman in storyData" :key="woman.id">
      <div class="card">
        <div class="pro-img">
           <img :src="woman.content.thumbnail" class="card-img-top croped" alt="mridufashion">
        </div>
        <div class="card-body">
          <h5 class="card-title">{{ woman.content.title }}</h5>
          <p class="card-text">{{ woman.content.summary.substring(0,100) }}</p>
          <h5 class="price float-right text-primary">{{woman.content.price}} Kr</h5>
        </div>

        <div class="card-footer bg-light">
           <router-link to="id"><a class="btn btn-outline-warning btn-sm text-dark">LIKE</a></router-link>
           <router-link :to="'/women/' + woman.id"><a class="btn btn-outline-success btn-sm ml-2">ADD TO BAG</a></router-link>
        </div>
     </div>
    </div>
  </div>
 </div>
</template>

<script>
import StoryblokClient from 'storyblok-js-client'
import axios from "axios";
import { log } from 'util';
const token = 'vzwC59CqmD9irvJTGSQVKAtt';
let storyapi = new StoryblokClient({
  accessToken: token
}) 
export default {
  name: 'Women',
  // data () {
  //   return {
  //     msg: 'Women Collections',
  //     story: { }
  //   }
  // },
  computed: {
    storyData(){
      return this.$store.getters.allWomenData;
    }    
  },
  mounted() {
    this.$store.dispatch('getStoryWomenData')
  }
  // mounted() {
  //     const token = 'vzwC59CqmD9irvJTGSQVKAtt';   
  //     axios.get(`https://api.storyblok.com/v1/cdn/stories?version=draft&token=${token}&starts_with=women`).then(res => {        
  //     console.log(res.data.stories);
  //     this.story = res.data.stories;  
  //   })
  //  }
  

  //   created () {
  //   window.storyblok.init({
  //     accessToken: token
  //   })
  //   window.storyblok.on('change', () => {
  //     this.getStory('women', 'draft')
  //   })
  //   window.storyblok.pingEditor(() => {
  //     if (window.storyblok.isInEditor()) {
  //       this.getStory.filter('women', 'draft')
  //     } else {
  //       this.getStory('women', 'draft')
  //     }
  //   })
  // },
  //   methods: {
  //   getStory(slug, version) {
  //     storyapi.get('cdn/stories/', {
  //       version: 'draft',
  //       starts_with: 'women/'
  //     })
  //     .then((response) => {
  //       console.log(response.data.stories);
        
  //       this.story = response.data.stories
  //     })
  //   }
  // }
}
</script>

<style lang="scss" scoped>
.pro-img{
    width: 100%;
    height: 250px;
    overflow: hidden;
}
</style>
