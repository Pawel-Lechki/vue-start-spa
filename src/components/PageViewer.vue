<template>
  <div class="container">
    <h1 class="emphesize">Page Title</h1>
    <p>Page Content</p>
    <p>{{ $route.params.index }}</p>
  </div>
</template>

<script>
  export default {
    created() {
      //   console.log(this.$route.params)
    },
  }
</script>
