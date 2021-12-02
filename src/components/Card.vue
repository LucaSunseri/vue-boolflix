<template>

    <div class="flip-card">
        <div class="flip-card-inner">
            <div class="flip-card-front">
                <img :src="image" :alt="title">
            </div>
            <div class="flip-card-back">
                <div v-if="title == originalTitle" class="title">
                    <p><span class="ls-text-card">Titolo: </span>{{title}}</p> 
                </div>
                <div v-else class="title">
                    <p><span class="ls-text-card">Titolo: </span>{{title}}</p> 
                    <p><span class="ls-text-card">Titolo originale: </span>{{originalTitle}}</p> 
                </div>
                <p><span class="ls-text-card">Lingua originale: </span><img class="flag" :alt="originalLanguage" :src="'http://purecatamphetamine.github.io/country-flag-icons/3x2/' + originalLanguage + `.svg`"></p>
                <!-- Change vote in stars -->
                <p v-if="voteAverage == 1"><span class="ls-text-card">Voto: </span> 
                    <span><b-icon icon="star-fill" font-scale="1"></b-icon></span>
                    <span v-for="index in 4" :key="index"><b-icon icon="star" font-scale="1"></b-icon></span>
                </p>
                <p v-else-if="voteAverage == 2"><span class="ls-text-card">Voto: </span> 
                    <span v-for="index in 2" :key="index"><b-icon icon="star-fill" font-scale="1"></b-icon></span>
                    <span v-for="index in 3" :key="index"><b-icon icon="star" font-scale="1"></b-icon></span>
                </p>
                <p v-else-if="voteAverage == 3"><span class="ls-text-card">Voto: </span> 
                    <span v-for="index in 3" :key="index"><b-icon icon="star-fill" font-scale="1"></b-icon></span>
                    <span v-for="index in 2" :key="index"><b-icon icon="star" font-scale="1"></b-icon></span>
                </p>
                <p v-else-if="voteAverage == 4"><span class="ls-text-card">Voto: </span> 
                    <span v-for="index in 4" :key="index"><b-icon icon="star-fill" font-scale="1"></b-icon></span>
                    <span><b-icon icon="star" font-scale="1"></b-icon></span>
                </p>
                <p v-else-if="voteAverage == 5"><span class="ls-text-card">Voto: </span>  
                    <span v-for="index in 5" :key="index"><b-icon icon="star-fill" font-scale="1"></b-icon></span>
                </p>
                <p v-else>
                    <span v-for="index in 5" :key="index"><b-icon icon="star" font-scale="1"></b-icon></span>
                </p>
                <p v-if="overview"><span class="ls-text-card">Trama: </span> <br> {{overview}}</p>
            </div>
         </div>
    </div>
  
</template>

<script>
export default {
    name: 'Card',
    props: {
        title: String,
        image: String,
        originalTitle: String,
        originalLanguage: String,
        voteAverage: Number,
        overview: String
    },

}
</script>

<style lang="scss" scoped>
@import '~bootstrap/dist/css/bootstrap.css';
@import '~bootstrap-vue/dist/bootstrap-vue.css';

.flip-card {
  background-color: transparent;
  width: 200px;
  height: 270px;
  perspective: 1000px;
  display: inline-block;
  padding: 2px;
  white-space: pre-wrap;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.flip-card-front {
  background-color: #bbb;
  color: black;
  img {
      width: 100%;
      height: 100%;
  }
}

.flip-card-back {
  background-color: #0a0a0ac4;
  color: white;
  transform: rotateY(180deg);
  overflow: auto;
  font-weight: bold;
  padding: 5px 2px;
}

.ls-text-card {
    font-size: 13px;
    color: gray;
}

.flag {
    margin-left: 5px;
    vertical-align: text-bottom;
    height: 25px;
    width: 25px;
}

</style>