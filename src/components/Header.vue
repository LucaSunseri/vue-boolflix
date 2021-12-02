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
                    <span><b-icon icon="search"></b-icon></span>
                    <input v-model.trim="toSearch" @keyup.enter="getInput" type="text" placeholder="Titoli">
                </div>
                <span><a href="#">Bambini</a></span>
                <span><b-icon icon="bell-fill" font-scale="1.3"></b-icon></span>
                <b-avatar src="https://placekitten.com/300/300"></b-avatar>
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
@import '~bootstrap/dist/css/bootstrap.css';
@import '~bootstrap-vue/dist/bootstrap-vue.css';

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 70px;
    color: #fff;
    background-color: rgba(0, 0, 0, 0.918);
    a:hover {
        color: #fff;
        filter: brightness(65%) !important;
    }  
}

.header__left {
    display: flex;
    align-items: center;
    margin-left: 50px;
    .logo {
        width: 10%;
        cursor: pointer;
        img {
            width: 100%;
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
    span {
        margin-left: 15px;
        cursor: pointer;
    }
}

.search-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 25px;
    border: 1px solid white;
    border-radius: 20px;
    span {
        margin-left: 10px;
    }
    input {
        border: 0;
        border-radius: 20px;
        padding: 0 10px;
        color: #fff;
        background-color: black;
        &:focus {
            outline: none;
        }
    }
}





</style>