<template>
  <Navbar :pages="pages" :active-page="activePage"></Navbar>
  <PageViewer v-if="pages.length > 0" :page="pages[activePage]"> </PageViewer>
  <create-page @page-created="pageCreated"></create-page>
</template>

<script>
  import PageViewer from "./components/PageViewer.vue"
  import Navbar from "./components/Navbar.vue"
  import { resolveTransitionHooks } from "vue"
  import CreatePage from "./components/CreatePage.vue"

  export default {
    components: {
      Navbar,
      PageViewer,
      CreatePage,
    },
    created() {
      this.getPages()

      this.$bus.$on("navbarLinkActived", (index) => {
        this.activePage = index
      })
    },
    data() {
      return {
        activePage: 0,
        pages: [],
      }
    },
    methods: {
      async getPages() {
        let res = await fetch("pages.json")
        let data = await res.json()

        this.pages = data
      },
      pageCreated(pageObj) {
        //console.log(pageObj)
        this.pages.push(pageObj)
      },
    },
  }
</script>
