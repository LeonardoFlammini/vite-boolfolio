<script>
export default {
  name: 'Navigator',
  props:{
    links: Array
  }
}
</script>


<template>
  <button
    class="btn btn-light me-2 "
    v-for="link in links"
    :key="link.label"
    v-html="link.label"
    :disabled="link.active || !link.url"
    @click="$emit('callApi', link.url)"
    ></button>
</template>



<style lang=" scss" scoped>

</style>