<template>
    <div>
        <Header @getToSearch="getToSearch"></Header>
        <Main :toSearch="input"></Main>
    </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
    name: 'App',
    components: {
        Header,
        Main
    },
    data() {
        return {
            input: '',
        }
    },
    methods: {
        getToSearch(input) {
            this.input = input;
        }
    }
}
</script>

<style lang="scss">
@import './assets/style/general.scss'

</style>