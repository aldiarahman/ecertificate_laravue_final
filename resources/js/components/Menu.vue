<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-dark">
        <a class="navbar-brand"><router-link :to="{name: 'home'}">
            ARS e-Certificate
        </router-link></a>


        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav ml-auto">
                <!--UNLOGGED-->
                <li v-if="!$auth.check()" v-for="(route, key) in routes.unlogged" v-bind:key="route.path">
                    <router-link  :to="{ name : route.path }" :key="key">
                        {{route.name}}
                    </router-link>
                    &nbsp;
                </li>
                <!--LOGGED USER-->
                <li v-if="$auth.check(1)" v-for="(route, key) in routes.user" v-bind:key="route.path">
                    <router-link  :to="{ name : route.path }" :key="key">
                        {{route.name}}
                    </router-link>
                    &nbsp;
                </li>
                <!--LOGGED ADMIN-->
                <li v-if="$auth.check(2)" v-for="(route, key) in routes.admin" v-bind:key="route.path">
                    <router-link  :to="{ name : route.path }" :key="key">
                        {{route.name}}
                    </router-link>
                    &nbsp;
                </li>

                <!--LOGOUT-->
                <li v-if="$auth.check()">
                    <a href="#" @click.prevent="$auth.logout()">Logout</a>
                </li>
            </ul>
        </div>
    </nav>

</template>

<script>
    export default {
        data() {
            return {
                routes: {
                    // UNLOGGED
                    unlogged: [
                        {
                            name: 'Register',
                            path: 'register'
                        },
                        {
                            name: 'Login',
                            path: 'login'
                        }
                    ],          // LOGGED USER
                    user: [
                        {
                            name: 'Dashboard',
                            path: 'dashboard'
                        }
                    ],
                    // LOGGED ADMIN
                    admin: [
                        {
                            name: 'Dashboard',
                            path: 'admin.dashboard'
                        }
                    ]
                }
            }
        },
        mounted() {
            //
        }
    }
</script>

