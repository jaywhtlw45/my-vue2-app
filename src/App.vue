<template>
    <div id="app">
       <EmailBox class="EmailBox"></EmailBox> 
    </div>
</template>

<script>
    import EmailBox from "./components/EmailBox.vue"

    export default {
        name: 'App',
        components: {
            EmailBox
        },
        data() {
            return {
                isCheckedParent: false,
            }
        },
    }
</script>

<style>
@import './styles/global.css';


#app {
    font-family: Avenir, Helvetica,
        Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>