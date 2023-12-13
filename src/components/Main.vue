<script>
import axios from 'axios';
import { store } from '../data/store';
import BlogComponent from './BlogComponent.vue';
import Loader from './Loader.vue'
import Navigator from './Navigator.vue'
export default {
  name: 'Main',
  components:{
    BlogComponent,
    Loader,
    Navigator
  },
  data(){
    return{
      title: 'ciao vue',
      store,
      isLoaded: false,
      links: []
    }
  },
  methods:{
    getApi(){
      axios.get(store.apiUrl + "get-projects")
        .then(results=>{
          store.projects = results.data.data;
          this.links = results.data.links
          this.isLoaded = true;
        })
    },
    callApi(linkUrl){
      axios.get(linkUrl)
        .then(results=>{
          store.projects = results.data.data;
          this.links = results.data.links
          this.isLoaded = true;
        })
    }
  },
  mounted(){
    this.getApi();
  }
}
</script>

<template>
  <div class="container-lf">
    <div
      class="d-flex justify-content-center align-items-center"
      v-if="!isLoaded"
      >
      <Loader/>
    </div>
    <div v-else>
      <BlogComponent />
      <Navigator
        :links="links"
        @callApi='callApi' />
    </div>
    
  </div>
</template>



<style scoped lang="scss">

</style>