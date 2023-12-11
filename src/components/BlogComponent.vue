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

</style>