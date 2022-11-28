<template>
    <div class="skeleton-card">
        <div class="skeleton skeleton-wrapper"></div>        
        <div class="skeleton-details">
            <h1 class="skeleton skeleton-title"></h1>
            <div class="skeleton skeleton-category"></div>
            <div class="skeleton-description">
                <p class="skeleton skeleton-text"></p>
                <p class="skeleton skeleton-text"></p>
                <p class="skeleton skeleton-text"></p>
                <p class="skeleton skeleton-text"></p>
                <p class="skeleton skeleton-text"></p>
                <p class="skeleton skeleton-text"></p>
            </div>
            <div class="skeleton-actions">
                <div class="skeleton skeleton-button"></div>
                <div class="skeleton skeleton-button"></div>
            </div>
        </div>        
    </div>
</template>
<script>
export default {
    name: 'ProductSkeleton'
}
</script>
<style>
   @import '../assets/style/product-skeleton.css';
</style>