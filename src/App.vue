<template>
    <div id="app">
        <img src="./assets/logo.png"/>
        <progress-bar :max="100" :current="progress"></progress-bar>
        <keep-alive>
            <component :is="template" @saved="sayHello" />
        </keep-alive>
        <div>
            <label>
                <input type="radio" name="page" @change="navigate('welcome')" :checked="currentPage == 'welcome'"/> Welcome
            </label>
            <label>
                <input type="radio" name="page" @change="navigate('form')" :checked="currentPage == 'form'"/> Form
            </label>
        </div>
    </div>
</template>

<script>
    import Register from './components/Register.vue';
    import Welcome from './components/Welcome.vue';
    import ProgressBar from './components/ProgressBar.vue';

    export default {
        name: 'app',

        data() {
            return {
                currentPage: 'welcome',
                progress: 0,
            }
        },

        components: {
            Register,
            Welcome,
            ProgressBar
        },

        methods: {
            sayHello(data) {
                console.log(data);
                alert(`hi, ${data.firstName} ${data.lastName}`);
                this.progress = 75;
            },
            navigate(page) {
                this.currentPage = page;

                switch(page) {
                    case 'welcome': this.progress = 0; break;
                    case 'form': this.progress = 50; break;
                    default: this.progress = 0; break;
                }
            }
        },

        computed: {

            template() {
                switch(this.currentPage) {
                    case 'welcome': return 'welcome'
                    case 'form' : return 'register'
                }

                return null;
            },
        }
    }

</script>

<style scoped>
    #app {
        max-width: 400px;
        margin: 0 auto;
    }
</style>