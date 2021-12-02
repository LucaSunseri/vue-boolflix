<template>
    <div>
        <div class="ls-card">
            <div class="ls-card__image">
               <img :src="image" :alt="title">
            </div>
            <div class="ls-card__hover"></div>
        </div>
    </div> 
</template>

<script>
export default {
    name: 'Card',
    props: {
        title: String,
        image: String,
    },

}
</script>

<style lang="scss" scoped>


</style>