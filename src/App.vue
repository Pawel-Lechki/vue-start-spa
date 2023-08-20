<template>
  <Navbar></Navbar>
  <!-- <PageViewer v-if="pages.length > 0" :page="pages[activePage]"> </PageViewer>
  <create-page @page-created="pageCreated"></create-page> -->
  <router-view></router-view>
</template>

<script>
  import PageViewer from "./components/PageViewer.vue"
  import Navbar from "./components/Navbar.vue"
  import CreatePage from "./components/CreatePage.vue"

  export default {
    components: {
      Navbar,
      PageViewer,
      CreatePage,
    },
    methods: {
      pageCreated(pageObj) {
        //console.log(pageObj)
        this.pages.push(pageObj)
      },
    },
  }
</script>
