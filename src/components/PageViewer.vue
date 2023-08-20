<template>
  <div v-if="page" class="container">
    <h1 class="emphesize">{{ page.pageTitle }}</h1>
    <p>{{ page.content }}t</p>
    <p>{{ $route.params.index }}</p>
  </div>
</template>

<script>
  export default {
    props: ["index"],
    created() {
      //   console.log(this.$route.params)
      //   this.page = this.$pages.getSinglePage(this.$route.params.index)
      this.page = this.$pages.getSinglePage(this.index)
      //   this.$watch(
      //     () => this.$route.params,
      //     (newParams, oldParams) =>
      //       (this.page = this.$pages.getSinglePage(newParams.index))
      //   )
    },
    data() {
      return {
        page: null,
      }
    },
    watch: {
      index(newIndex, oldIndex) {
        this.page = this.$pages.getSinglePage(newIndex)
      },
    },
  }
</script>
