<script>
import {store} from '../data/store'
export default {
  name:'BlogComponent',
  data(){
    return{
      store
    }
  }
}
</script>


<template>
  <h1>I miei proggetti</h1>
  <table class="table">
  <thead>
    <tr>
      <th scope="col">id</th>
      <th scope="col">Title</th>
      <th scope="col">Date</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="project in store.projects" :key="project.id">
      <th >{{project.id}}</th>
      <td>{{project.title}}</td>
      <td>{{project.creation_date}}</td>
    </tr>
  </tbody>
</table>
</template>


<style lang="scss">
h1{
  color: white;
  font-weight: bold;
}
</style>