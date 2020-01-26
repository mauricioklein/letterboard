<template>
  <div class="error">
    <p v-for="(count, char) in missing" :key="char">
      Missing {{ count }} {{ char }}'s
    </p>
  </div>
</template>

<script>
export default {
  name: 'Error',
  props: {
    missing: Object
  }
}
</script>
