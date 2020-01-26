<template>
  <div class="result">
    <Success v-if="noMissing" />
    <Error v-else :missing="missing" />
  </div>
</template>

<script>
import Success from './Success.vue'
import Error from './Error.vue'

export default {
  name: 'Result',
  props: {
    missing: Object
  },
  components: {
    Success,
    Error
  },
  computed: {
    noMissing: function() {
      return Object.keys(this.missing).length == 0
    }
  }
}
</script>
