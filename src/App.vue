<template>
    <div id="app">
        <img src="./assets/logo.png"/>
        <progress-bar :max="100" :current="currentProgress"></progress-bar>
        <component :is="template" @saved="sayHello" />
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
            },
            navigate(page) {
                this.currentPage = page;
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
            currentProgress() {
                switch(this.currentPage) {
                    case 'welcome': return 0;
                    case 'form' : return 50;
                }

                return 0;
            }
        }
    }

</script>

<style scoped>
    #app {
        max-width: 400px;
        margin: 0 auto;
    }
</style>