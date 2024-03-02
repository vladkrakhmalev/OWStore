<script setup>
  import { ref } from 'vue'

  const props = defineProps(['product'])
  const addedToCart = ref(false)
  const addedToFavorite = ref(false)
  const selectedColor = ref(props.product.colors[0].value)
  const selectedSize = ref(props.product.sizes[0].value)
  const baseUrl = ref(import.meta.env.BASE_URL)

  function addToFavorite() {
    this.addedToFavorite = !this.addedToFavorite
  }

  function addToCart() {
    const formData = {
      color: this.selectedColor,
      size: this.selectedSize
    }
    console.log('Отправляем данные в корзину:', formData);
    this.addedToCart = true
  }
</script>

<template>
  <form class="product__form" @submit.prevent="addToCart()">
    <div class="product__info">
      <div class="product__title">
        <h1>{{ product.name }}</h1>
        <p class="product__article">{{ product.article }}</p>
      </div>
      <div class="product__price">
        <p class="product__price-new">{{ product.newPrice.toLocaleString() }} ₽</p>
        <p class="product__price-old">{{ product.oldPrice.toLocaleString() }} ₽</p>
      </div>
      <p class="product__text">{{ product.description }}</p>
    </div>

    <div class="product__field">
      <h5>Выберите цвет: <span id="color_value">{{ selectedColor }}</span></h5>
      <div class="product__colors">
        <label
          v-for="color in product.colors"
          @click="$emit('changeColor', color.images)"
          class="product__color"
          :class="color.quantity === 0 ? '_hidden' : ''"
        >
          <input
            type="radio"
            name="color"
            :value="color.value"
            class="product__color-input"
            v-model="selectedColor"
          />
          <img :src="baseUrl + color.image" alt="" class="product__color-img"/>
        </label>
      </div>
    </div>
    
    <div class="product__field">
      <h5>Выберите размер: <span id="size_value">{{ selectedSize }}</span></h5>
      <div class="product__sizes">
        <label class="product__size" v-for="size in product.sizes">
          <input 
            type="radio"
            name="size"
            class="product__size-input"
            :value="size.value"
            :disabled="size.quantity === 0"
            v-model="selectedSize"
          />
          <p class="product__size-value">{{ size.value }}</p>
        </label>
      </div>
    </div>

    <div>
      <a href="/size-chart" class="product__link">Таблица размеров</a>
      <div class="product__buttons">
        <button type="submit" class="button _primary" :disabled="addedToCart">
          {{ addedToCart ? 'Товар в корзине' : 'Добавить в корзину' }}
        </button>
        <button
          type="button"
          class="button _secondary _favorite"
          :class="addedToFavorite ? '_active' : ''"
          @click="addToFavorite()"
        >В избранное</button>
      </div>
    </div>
  </form>
</template>

<style>

  .product__form {
    display: grid;
    gap: 32px;
    align-content: start;
  }

  .product__info {
    display: grid;
    gap: 16px;
  }

  .product__title {
    display: flex;
    column-gap: 16px;
    flex-wrap: wrap;
  }

  .product__article {
    color: #898D8D;
    align-self: end;
    margin-bottom: 2px;
  }

  .product__price {
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .product__price-new {
    line-height: 1;
    font-weight: bold;
    padding: 3px 8px;
    background-color: #FFC72C;
    border-radius: 3px;
  }

  .product__price-old {
    color: #898D8D;
    text-decoration: line-through;
    line-height: 1;
  }

  .product__field {
    display: grid;
    gap: 12px;
  }

  .product__colors {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .product__color {
    width: 32px;
    height: 32px;
    border-radius: 50%;
    cursor: pointer;
  }

  .product__color._hidden {
    display: none;
  }

  .product__color-img {
    width: 100%;
    border-radius: 50%;
    border: 3px solid #ffffff00;
    outline: 1px solid #38383B00;
    transition: .1s;
  }

  .product__color:hover > .product__color-img,
  .product__color-input:checked + .product__color-img {
    border: 3px solid #ffffffff;
    outline: 1px solid #38383Bff;
  }

  .product__color-input {
    display: none;
  }

  .product__sizes {
    display: flex;
    flex-wrap: wrap;
  }

  .product__size {
    width: 50px;
    text-align: center;
  }

  .product__size-input {
    display: none;
  }

  .product__size:hover > .product__size-value,
  .product__size-input:checked + .product__size-value {
    background-color: #38383B;
    color: #fff;
  }

  .product__size-input:disabled + .product__size-value {
    color: #898D8D;
    cursor: default;
    background-color: #fff;
    background-image: url('../img/cross.svg');
    background-repeat: no-repeat;
    background-size: 100%;
    background-position: center;
  }
  
  .product__size-value {
    border: 1px solid #ccc;
    padding: 10px 13px;
    font-size: 14px;
    line-height: 18px;
    cursor: pointer;
    transition: .2s;
  }

  .product__link {
    display: block;
    color: #38383B;
    transition: .2s;
    font-size: 14px;
    margin-bottom: 16px;
  }

  .product__link:hover {
    color: #FFC72C;
  }

  .product__buttons {
    display: grid;
    grid-template-columns: 1fr auto;
    column-gap: 8px;
  }

  @media (max-width: 768px) {

    .product__form {
      gap: 24px;
    }

    .product__info {
      padding-bottom: 24px;
      border-bottom: 1px solid #ccc;
    }

    .product__article {
      font-size: 14px;
      line-height: 22px;
    }

    .product__text {
      display: none;
    }

    .product__field {
      gap: 8px;
    }

    .product__link {
      margin-bottom: 8px;
    }
  }

</style>
