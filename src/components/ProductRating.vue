<template>
    <div class="ratings">
        <span class="ratings-rate">{{`${rate}/${maxRatings}`}}</span>
        <div class="ratings-container" v-for="rating in maxRatings" :key="rating"> 
            <div 
                class="rating" 
                :class="rating <= ratingRounded ? ratingActiveClass : ratingClass"
            >
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'ProductRating',
    props: ['rate', 'maxRatings', 'isMenCategory'],
    computed: {
        ratingRounded(){
            return Math.round(this.rate)
        },
        ratingActiveClass(){
            return this.isMenCategory ? 'rating-active-men' : 'rating-active-women'
        },
        ratingClass(){
            return this.isMenCategory ? 'rating-men' : 'rating-women'
        }

    }
}
</script>
<style>
    @import '../assets/style/product-rating.css';
</style>