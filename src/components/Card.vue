<template>
    <div>
        <div class="card">
            <div class="card__image">
               <img :src="image" :alt="title">
            </div>
            <div class="card__hover"></div>
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