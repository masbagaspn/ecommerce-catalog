<template>
    <section class="card">
        <div class="card-wrapper">
            <img class="card-image" :src="details.image"/>
        </div>
        <div class="card-details">
            <div class="card-header">
                <h1 
                    class="card-title"
                    :class="isMenCategory ? 'card-title-men' : 'card-title-women'"
                >
                    {{ details.title }}
                </h1>
                <div class="card-wrapper-2">
                    <div class="card-category-rating">
                        <span class="card-category">{{ details.category }}</span>
                        <ProductRating 
                            :rate="details.rating.rate" 
                            :maxRatings="5" 
                            :isMenCategory="isMenCategory" 
                        />
                    </div>
                    <hr />
                </div>
            </div>
            <p class="card-description" >{{ limitDescription }}</p>
            <div class="card-footer">
                <hr />
                <p 
                    class="card-price"
                    :class="isMenCategory ? 'card-price-men' : 'card-price-women' "
                >
                    {{ priceInDollarUSD }}
                </p>
                <div class="card-actions">
                    <button 
                        class="button button-primary"
                        :class="isMenCategory ? 'button-primary-men' : 'button-primary-women' "
                        >
                        Buy Now
                    </button>
                    <button 
                        class="button button-secondary" 
                        @click="$emit('increase-index')"
                        :class="isMenCategory ? 'button-secondary-men' : 'button-secondary-women' "
                    >
                        Next Product
                    </button>
                </div>
            </div>
        </div>
    </section>
</template>
<script>
import ProductRating from './ProductRating.vue';

export default {
    name: 'ProductAvailable',
    props: {
        details: Object,
    },
    components: {
        ProductRating
    },
    computed: {
        isMenCategory() {
            return this.details.category === "men's clothing"
        },
        priceInDollarUSD() {
            return `$${this.details.price}`
        },
        splitDescription() {
            return this.details.description.split('')
        },
        limitDescription() {
            return this.splitDescription.length > 500 ? `${this.splitDescription.slice(0, 500).join('')}...` : this.details.description 
        }
    }
}
</script>
<style>
    @import '../assets/style/product-available.css';
</style>