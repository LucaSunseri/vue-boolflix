<template>
    <div>

        <header>
            <div class="header__left">LOGO</div>
            <div class="header__right">
                <input v-model="toSearch" @keyup.enter="getInput" type="text">
                <button @click="getInput">Cerca</button>
            </div>
        </header>
        
    </div>  
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            toSearch: '',
        }
    },
    methods: {
        getInput() {
            this.$emit('getToSearch', this.toSearch)
        }
    }
}
</script>

<style lang="scss" scoped>

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 80px;
    background-color: rgba(49, 49, 49, 0.527);
}

.header__right {
    margin-right: 15px;
}

</style>