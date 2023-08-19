<template>
    <nav :class="[`navbar-${theme}`, `bg-${theme}`, 'navbar', 'navbar-expand-lg']">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">My Vue</a>
            <div class="container-fluid" id="navbarNav">
            <ul class="navbar-nav">
                <li v-for="(page, index) in pages" class="nav-item active" :key="index">
                    <a
                        class="nav-link" 
                        :class="{active: activePage == index}"
                        aria-current="page"
                        :href="page.link.url"
                        :title="`This link goes to the ${page.link.text} page`"
                        @click.prevent="navLinkClick(index)"
                    >
                        {{  page.link.text }}
                    </a>
                </li>
            </ul>
            </div>
        </div>
        <form class="d-flex me-2">
            <button class="btn btn-primary" @click.prevent="changeTheme()">Toggle</button>
        </form>
    </nav>   
</template>

<script>
    export default {
        props: ['pages', 'activePage', 'navLinkClick'],
        data() {
            return {
                theme: 'dark'
            }
        },
        methods: {
            changeTheme() {
                let theme = 'light';

                if(this.theme == 'light') {
                    theme = 'dark';
                }

                this.theme = theme;
            }
        }
    }
</script>