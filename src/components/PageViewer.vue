<template>
  <div class="container">
    <h1 class="emphesize">Page Title</h1>
    <p>Page Content</p>
  </div>
</template>

<script>
  export default {
    props: {
      page: {
        type: Object,
        default(rawProps) {
          return {
            pageTitle: "",
            content: "",
          }
        },
      },
    },
  }
</script>
