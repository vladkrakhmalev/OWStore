<template>
  <main class="product">
    <div class="container product__container">
      <Breadcrumbs />
      <ProductGallery />
      <ProductDetails />
    </div>
  </main>
</template>

<script>
import Breadcrumbs from './Breadcrumbs.vue'
import ProductGallery from './ProductGallery.vue'
import ProductDetails from './ProductDetails.vue'

export default {
  components: {
    Breadcrumbs,
    ProductGallery,
    ProductDetails,
  }
}
</script>

<style>
  .product {
    padding: 24px 0 96px;
  }

  .product__container {
    display: grid;
    grid-template: auto/minmax(0, 1fr) 1fr;
    row-gap: 24px;
    column-gap: 40px;
  }

  @media (max-width: 1024px) {
    .product {
      padding: 24px 0 61px;
    }
    .product__container {
      column-gap: 20px;
    }
  }

  @media (max-width: 768px) {
    .product {
      padding: 0 0 26px;
    }

    .product__container {
      grid-template-columns: minmax(0, 1fr);
    }
  }
</style>
