<script>
import axios from 'axios';
import { store } from '../data/store';
import BlogComponent from './BlogComponent.vue';
export default {
  name: 'Main',
  components:{
    BlogComponent
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
          store.projects = results.data;
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
      <BlogComponent />
  </div>
</template>



<style scoped lang="scss">

</style>