<template>
    <div>

        <header>
            <div class="header__left">
                <div class="logo">
                    <img src="https://image.tmdb.org/t/p/original/wwemzKWzjKYJFfCeiB57q3r4Bcm.svg" alt="Logo">
                </div>
                <div class="menu">
                    <ul>
                        <li><a href="#">Home</a></li>
                        <li><a href="#">Serie Tv</a></li>
                        <li><a href="#">Film</a></li>
                        <li><a href="#">Nuovi e Popolari</a></li>
                    </ul>
                </div>
            </div>
            <div class="header__right">
                <div class="search-bar">
                    <i class="fas fa-search" title="Cerca..."></i>
                    <input v-model.trim="toSearch" @keyup.enter="getInput" type="text" placeholder="Titoli">
                </div>
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
    color: #fff;
    background-color: black;
}

.header__left {
    display: flex;
    align-items: center;
    margin-left: 50px;
    .logo {
        width: 10%;
        img {
            width: 80%;
        }
    }
    .menu {
        li {
            margin-left: 15px;
        }
    }
}

.header__right {
    display: flex;
    align-items: center;
    margin-right: 50px;
}

.search-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 30px;
    margin: 5px 15px;
    border: 1px solid white;
    border-radius: 20px;
}

.search-bar i {
    margin: 0 10px;
}

.search-bar i:hover {
    cursor: pointer;
}

.search-bar input {
    width: 100%;
    height: 100%;
    border: 0;
    border-radius: 20px;
    padding: 0 10px;
    color: #fff;
    background-color: black;
}

.search-bar input:focus {
    outline: none;
}


</style>