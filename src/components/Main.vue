<script>
import axios from 'axios';
import { store } from '../data/store';
import BlogComponent from './BlogComponent.vue';
import Loader from './Loader.vue'
export default {
  name: 'Main',
  components:{
    BlogComponent,
    Loader
  },
  data(){
    return{
      title: 'ciao vue',
      store,
      isLoaded: false
    }
  },
  methods:{
    getApi(){
      axios.get(store.apiUrl + "get-projects")
        .then(results=>{
          store.projects = results.data.data;
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
    <BlogComponent v-else/>
  </div>
</template>



<style scoped lang="scss">

</style>