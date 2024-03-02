<script setup>
  defineProps(['product'])
</script>

<template>
  <div class="breadcrumbs">
    <a href="/catalog" class="breadcrumbs__link">Каталог</a>
    <a href="/jackets-kids" class="breadcrumbs__link">Куртки и пальто для малышей</a>
    <p class="breadcrumbs__item">{{product.name}}</p>
  </div>
</template>

<style>
  .breadcrumbs {
    grid-column: 1/-1;
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
  }

  .breadcrumbs__item,
  .breadcrumbs__link {
    font-size: 14px;
    color: #898D8D;
    text-decoration: none;
    transition: .1s;
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .breadcrumbs__link:hover {
    color: #FFC72C
  }

  .breadcrumbs__link:not(:last-child)::after {
    content: '';
    display: block;
    width: 5px;
    height: 7px;
    background-image: url('../img/icon-arrow.svg');
    background-repeat: no-repeat;
    background-size: contain;
    background-position: center;
  }

  @media (max-width: 768px) {
    .breadcrumbs {
      display: none;
    }
  }
</style>
