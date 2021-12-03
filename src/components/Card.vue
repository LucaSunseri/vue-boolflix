<template>

    <div class="flip-card">
        <div class="flip-card-inner">
            <!-- Section Image -->
            <div v-if="image" class="flip-card-front">
                <img :src="`${imageUrl}${image}`" :alt="title">
            </div>
            <div v-else class="flip-card-front">
                <img class="ls-img-default" src="../assets/img/default.jpg">
                <h3 class="ls-text-default">{{title}}</h3>
            </div>
            <div class="flip-card-back">
                <!-- Section Title (Title is the same from Original Title)-->
                <div v-if="title == originalTitle" class="title">
                    <p><span class="ls-text-card">Titolo: </span>{{title}}</p> 
                </div>
                <!-- Section Title (Title different from Original Title) -->
                <div v-else class="title">
                    <p><span class="ls-text-card">Titolo: </span>{{title}}</p> 
                    <p><span class="ls-text-card">Titolo originale: </span>{{originalTitle}}</p> 
                </div>
                <!-- Section Language -->
                <div><span class="ls-text-card">Lingua originale: </span><img class="flag" :alt="originalLanguage" :src="'http://purecatamphetamine.github.io/country-flag-icons/3x2/' + originalLanguage + `.svg`"></div>
                <!-- Section Stars (Change vote in stars) -->
                <div><span class="ls-text-card">Voto: </span> 
                    <b-icon v-for="index in voteAverage" :key="index + `A`" icon="star-fill" font-scale="1"></b-icon>
                    <b-icon v-for="index in (5-voteAverage)" :key="index + `B`" icon="star" font-scale="1"></b-icon>
                </div>
                <!-- Section Overview -->
                <div v-if="overview"><span class="ls-text-card">Trama: </span> <br> <p class="ls-overview">{{overview}}</p></div>
            </div>
         </div>
    </div>
  
</template>

<script>
export default {
    name: 'Card',
    data() {
        return {
            imageUrl: 'https://image.tmdb.org/t/p/w185/',
        }
    },
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
  div {
       margin-bottom: 5px;
      p {
          margin-bottom: 5px;
      }
  }
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
  font-weight: bold;
  padding: 5px 2px;
  font-size: 12px;
  overflow: auto;
}

.ls-text-card {
    font-size: 11px;
    color: gray;
}

.ls-overview {
    line-height: 1rem;
    margin-top: -10px;
    padding: 0;
}

.flag {
    margin-left: 5px;
    vertical-align: text-bottom;
    height: 20px;
    width: 22px;
}

.ls-img-default {
    filter: opacity(35%);
}

.ls-text-default {
    position: absolute;
    top: 2%;
    left: 50%;
    transform: translatex(-50%);
    text-align: center;
}

</style>