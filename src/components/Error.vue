<template>
  <div>
    <v-alert type="error" dense v-for="(count, char) in missing" :key="char" >
      Missing {{ count }} {{ char }}'s
    </v-alert>
  </div>
</template>

<script>
  import Vue from 'vue'

  export default Vue.component('Error', {
    props: {
      missing: Object
    }
  })
</script>
