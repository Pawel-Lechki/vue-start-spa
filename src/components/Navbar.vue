<template>
  <nav
    :class="[`navbar-${theme}`, `bg-${theme}`, 'navbar', 'navbar-expand-lg']"
  >
    <div class="container-fluid">
      <a class="navbar-brand" href="#">My Vue</a>
      <div class="container-fluid" id="navbarNav">
        <ul class="navbar-nav">
          <navbar-link
            v-for="(page, index) in publishedPages"
            class="nav-item"
            :key="index"
            :page="page"
            :index="index"
            :isActive="active === index"
            @actived="$emit('actived')"
          ></navbar-link>
          <li>
            <router-link to="/create" class="nav-link" aria-current="page">
              Create Page
            </router-link>
          </li>
        </ul>
      </div>
    </div>
    <form class="d-flex me-2">
      <button class="btn btn-primary" @click.prevent="changeTheme()">
        Toggle
      </button>
    </form>
  </nav>
</template>

<script>
  import NavbarLink from "./NavbarLink.vue"
  export default {
    components: {
      NavbarLink,
    },
    created() {
      this.getThemeSetting()
    },
    computed: {
      publishedPages() {
        return this.pages.filter((p) => p.published)
      },
    },
    props: ["pages", "activePage"],
    data() {
      return {
        theme: "dark",
      }
    },
    methods: {
      changeTheme() {
        let theme = "light"

        if (this.theme == "light") {
          theme = "dark"
        }

        this.theme = theme
        this.storeThemeSetting()
      },
      storeThemeSetting() {
        localStorage.setItem("theme", this.theme)
      },
      getThemeSetting() {
        let theme = localStorage.getItem("theme")

        if (theme) {
          this.theme = theme
        }
      },
    },
  }
</script>
