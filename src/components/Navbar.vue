<template>
    <nav :class="[`navbar-${theme}`, `bg-${theme}`, 'navbar', 'navbar-expand-lg']">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">My Vue</a>
            <div class="container-fluid" id="navbarNav">
            <ul class="navbar-nav">
                <li v-for="(page, index) in pages" class="nav-item active" :key="index">
                   <navbar-link 
                        :page="page" 
                        :isActive="active === index"         
                        @click.prevent="navLinkClick(index)"></navbar-link>
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
    import NavbarLink from './NavbarLink.vue';
    export default {
        components: {
            NavbarLink
        },
        created() {
            this.getThemeSetting();
        },
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
                this.storeThemeSetting();
            },
            storeThemeSetting() {
                localStorage.setItem('theme', this.theme);
            },
            getThemeSetting() {
                let theme = localStorage.getItem('theme');

                if (theme) {
                    this.theme = theme;
                }
            },
        }
    }
</script>