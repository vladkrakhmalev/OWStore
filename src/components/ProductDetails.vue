<template>
  <form class="product__form">
    <div class="product__info">
      <div class="product__title">
        <h1>Зимняя куртка</h1>
        <p class="product__article">арт.: winter-23324-12</p>
      </div>
      <div class="product__price">
        <p class="product__price-new">5 499 ₽</p>
        <p class="product__price-old">6 200 ₽</p>
      </div>
      <p class="product__text">Детская классическая куртка изготовлена из водо- и ветронепроницаемого материала softshell с грязеотталкивающей поверхностью.</p>
    </div>

    <div class="product__field">
      <h5>Выберите цвет: <span id="color_value">оранжевый</span></h5>
      <div class="product__colors">
        <label class="product__color">
          <input type="radio" name="color" value="оранжевый" class="product__color-input" checked/>
          <img src="../img/color-1.png" alt="" class="product__color-img">
        </label>
        <label class="product__color">
          <input type="radio" name="color" value="розовый"  class="product__color-input"/>
          <img src="../img/color-2.png" alt="" class="product__color-img">
        </label>
        <label class="product__color">
          <input type="radio" name="color" value="фиолетовый"  class="product__color-input"/>
          <img src="../img/color-3.png" alt="" class="product__color-img">
        </label>
        <label class="product__color">
          <input type="radio" name="color" value="синий"  class="product__color-input"/>
          <img src="../img/color-4.png" alt="" class="product__color-img">
        </label>
        <label class="product__color">
          <input type="radio" name="color" value="зеленый"  class="product__color-input"/>
          <img src="../img/color-5.png" alt="" class="product__color-img">
        </label>
      </div>
    </div>
    
    <div class="product__field">
      <h5>Выберите размер: <span id="size_value">104</span></h5>
      <div class="product__sizes">
        <label class="product__size">
          <input type="radio" name="size" value="92" class="product__size-input"/>
          <p class="product__size-value">92</p>
        </label>
        <label class="product__size">
          <input type="radio" name="size" value="98"  class="product__size-input"/>
          <p class="product__size-value">98</p>
        </label>
        <label class="product__size">
          <input type="radio" name="size" value="104"  class="product__size-input" checked/>
          <p class="product__size-value">104</p>
        </label>
        <label class="product__size">
          <input type="radio" name="size" value="110"  class="product__size-input"/>
          <p class="product__size-value">110</p>
        </label>
        <label class="product__size">
          <input type="radio" name="size" value="116"  class="product__size-input"/>
          <p class="product__size-value">116</p>
        </label>
        <label class="product__size">
          <input type="radio" name="size" value="122"  class="product__size-input"/>
          <p class="product__size-value">122</p>
        </label>
        <label class="product__size">
          <input type="radio" name="size" value="128"  class="product__size-input"/>
          <p class="product__size-value">128</p>
        </label>
        <label class="product__size">
          <input type="radio" name="size" value="134" disabled  class="product__size-input"/>
          <p class="product__size-value">134</p>
        </label>
        <label class="product__size">
          <input type="radio" name="size" value="140" disabled  class="product__size-input"/>
          <p class="product__size-value">140</p>
        </label>
      </div>
    </div>

    <div>
      <a href="/size-chart" class="product__link">Таблица размеров</a>
      <div class="product__buttons">
        <button type="submit" class="button _primary">Добавить в корзину</button>
        <button class="button _secondary _favorite">В избранное</button>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  
}
</script>

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

  .product__color-img {
    width: 100%;
    border-radius: 50%;
    border: 3px solid #ffffff00;
    outline: 1px solid #38383B00;
    transition: .1s;
  }

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
    cursor: pointer;
    width: 50px;
    text-align: center;
  }

  .product__size-input:disabled + .product__size-value {
    color: #898D8D;
  }

  .product__size-input {
    display: none;
  }

  .product__size-input:checked + .product__size-value {
    background-color: #38383B;
    color: #fff;
  }
  
  .product__size-value {
    border: 1px solid #ccc;
    padding: 10px 13px;
    font-size: 14px;
    line-height: 18px;
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

    .product__sizes {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(50px, 1fr));;
    }

    .product__size {
      width: 100%;
    }

    .product__link {
      margin-bottom: 8px;
    }
  }

</style>
