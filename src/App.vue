<template>
    <Navbar :pages="pages" :active-page="activePage" :nav-link-click="(index) => activePage = index"></Navbar>
    <PageViewer :page="pages[activePage]"></PageViewer>
</template>

<script>
    import PageViewer from './components/PageViewer.vue';
    import Navbar from './components/Navbar.vue';

    export default{
        components: {
            Navbar,
            PageViewer
        },
        data() {
            return {
                activePage: 0,
                pages: [
                    {
                        link: {text: 'Home', url: 'index.html'},
                        pageTitle: 'Home Page',
                        content: 'This in the home page content'
                    },
                    {
                        link: {text: 'About', url: 'index.html'},
                        pageTitle: 'About Page',
                        content: 'This in the about page content'
                    },
                    {
                        link: {text: 'Contact', url: 'index.html'},
                        pageTitle: 'Contact Page',
                        content: 'This in the contact page content'
                    },
                ],
            }
        }
    }
</script>