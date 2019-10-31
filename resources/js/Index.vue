<template>
    <div id="main">
        <header id="header">
            <navigationMenu></navigationMenu>
        </header>
        <br><br>
        <div id="content">
            <router-view></router-view>
        </div>
    </div>
</template>

<script>
    import navigationMenu from './components/Menu.vue'
    export default {
        data() {
            return {
                //
            }
        },
        components: {
            navigationMenu
        }
    }
</script>

<style scoped>

</style>
