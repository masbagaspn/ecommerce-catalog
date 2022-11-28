<template>
    <div class="unavailable-card">
        <div class="unavailable-actions">
            <span>This product is unavailable to show</span>
            <button 
                class="button button-secondary"
                @click="$emit('increase-index')"
            >
                Next Product
            </button>
        </div>
    </div>
</template>
<script>
export default {
    name: "ProductUnavailable"
}
</script>
<style>
    @import '../assets/style/product-unavailable.css'
</style>