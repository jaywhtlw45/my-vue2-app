
<template>
    <div id="app">
        <img
            alt="Vue logo"
            src="./assets/logo.png"
        />
        <HelloWorld
            msg="Welcome to Your Vue.js App"
        />
        <CheckBox
            :isCheckedParent.sync="
                isCheckedParent
            "
        ></CheckBox>
        <div v-if="isCheckedParent">
            Hello from parent!
        </div>
    </div>
</template>

<script>
    import CheckBox from './components/CheckBox.vue'

    export default {
        name: 'App',
        components: {
            CheckBox,
        },
        data() {
            return {
                isCheckedParent: false,
            }
        },
    }
</script>

<style>
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
