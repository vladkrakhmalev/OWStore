<script setup>
import Breadcrumbs from './Breadcrumbs.vue'
import ProductGallery from './ProductGallery.vue'
import ProductDetails from './ProductDetails.vue'
import { ref } from 'vue'

const product = {
  name: 'Зимняя куртка',
  article: 'арт.: winter-23324-12',
  oldPrice: 6200,
  newPrice: 5499,
  discount: 20,
  description: 'Детская классическая куртка изготовлена из водо- и ветронепроницаемого материала softshell с грязеотталкивающей поверхностью.',
  colors: [
    { value: 'оранжевый', image: 'color-1.png', quantity: 10, images: ['image-red-1.png', 'image-red-2.png', 'image-red-3.png']},
    { value: 'розовый', image: 'color-2.png', quantity: 15, images: ['image-red-1.png', 'image-red-2.png', 'image-red-3.png'] },
    { value: 'фиолетовый', image: 'color-3.png', quantity: 20, images: ['image-blue-1.png', 'image-blue-2.png', 'image-blue-3.png'] },
    { value: 'синий', image: 'color-4.png', quantity: 5, images: ['image-blue-1.png', 'image-blue-2.png', 'image-blue-3.png'] },
    { value: 'зеленый', image: 'color-5.png', quantity: 15, images: ['image-green-1.png', 'image-green-2.png', 'image-green-3.png'] },
    { value: 'серый', image: 'color-5.png', quantity: 0, images: ['image-big-1.png', 'image-big-2.png', 'image-big-3.png'] }
  ],
  sizes: [
    { value: 92, quantity: 10 },
    { value: 98, quantity: 15 },
    { value: 104, quantity: 20 },
    { value: 110, quantity: 20 },
    { value: 116, quantity: 20 },
    { value: 122, quantity: 10 },
    { value: 128, quantity: 15 },
    { value: 134, quantity: 0 },
    { value: 140, quantity: 0 }
  ]
}

const activeGallery = ref(product.colors[0].images)

</script>

<template>
  <main class="product">
    <div class="container product__container">
      <Breadcrumbs :product="product"/>
      <ProductGallery :images='activeGallery' :product="product"/>
      <ProductDetails @changeColor='images => activeGallery = images' :product="product"/>
    </div>
  </main>
</template>

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
