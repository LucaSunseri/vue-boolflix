<template>

    <div class="flip-card">
        <div class="flip-card-inner">
            <div class="flip-card-front">
                <img :src="image" :alt="title">
            </div>
            <div class="flip-card-back">
            <p>{{title}}</p> 
            <p>{{originalTitle}}</p> 
            <p>Lingua: <img class="flag" :alt="originalLanguage" :src="'http://purecatamphetamine.github.io/country-flag-icons/3x2/' + originalLanguage + `.svg`"></p>
            <p v-if="voteAverage == 1">Voto: 
                <span><b-icon icon="star-fill" font-scale="1"></b-icon></span>
                <span v-for="index in 4" :key="index"><b-icon icon="star" font-scale="1"></b-icon></span>
            </p>
            <p v-else-if="voteAverage == 2">Voto: 
                <span v-for="index in 2" :key="index"><b-icon icon="star-fill" font-scale="1"></b-icon></span>
                <span v-for="index in 3" :key="index"><b-icon icon="star" font-scale="1"></b-icon></span>
            </p>
            <p v-else-if="voteAverage == 3">Voto: 
                <span v-for="index in 3" :key="index"><b-icon icon="star-fill" font-scale="1"></b-icon></span>
                <span v-for="index in 2" :key="index"><b-icon icon="star" font-scale="1"></b-icon></span>
            </p>
            <p v-else-if="voteAverage == 4">Voto: 
                <span v-for="index in 4" :key="index"><b-icon icon="star-fill" font-scale="1"></b-icon></span>
                <span><b-icon icon="star" font-scale="1"></b-icon></span>
            </p>
            <p v-else-if="voteAverage == 5">Voto: 
                <span v-for="index in 5" :key="index"><b-icon icon="star-fill" font-scale="1"></b-icon></span>
            </p>
            <p v-else>
                <span v-for="index in 5" :key="index"><b-icon icon="star" font-scale="1"></b-icon></span>
            </p>
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
  text-align: center;
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
  background-color: #2980b9;
  color: white;
  transform: rotateY(180deg);
}

</style>