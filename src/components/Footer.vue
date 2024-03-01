<template>
  <footer class="footer">
    <nav class="container footer__menu">
      <div class="footer__column" :class="{'_open': activeIndex === 1}">
        <div @click="toggleAccordion(1, $event)" class="footer__column-name">Магазин</div>
        <div class="footer__column-content" :style="{height: activeIndex === 1 ? activeHeight + 'px' : 0}">
          <a href="/about" class="footer__link">О нас</a>
          <a href="/history" class="footer__link">История</a> 
        </div>
      </div>
      <div class="footer__column _big" :class="{'_open': activeIndex === 2}">
        <div @click="toggleAccordion(2, $event)" class="footer__column-name">Покупателю</div>
        <div class="footer__column-content" :style="{height: activeIndex === 2 ? activeHeight + 'px' : 0}">
          <a href="/payment-and-delivery" class="footer__link">Оплата и доставка</a>
          <a href="/return" class="footer__link">Возврат товара и денег</a> 
          <a href="/size-chart" class="footer__link">Таблица размеров</a> 
          <a href="/care" class="footer__link">Уход за вещами</a> 
        </div>
      </div>
      <div class="footer__column" :class="{'_open': activeIndex === 3}">
        <div @click="toggleAccordion(3, $event)" class="footer__column-name">Контакты</div>
        <div class="footer__column-content" :style="{height: activeIndex === 3 ? activeHeight + 'px' : 0}">
          <a href="tel:88008881204" class="footer__link">8 800 888-12-04</a>
          <a href="mailto:order@shop.ru" class="footer__link _small">order@shop.ru</a> 
          <p class="footer__item">Москва, ул. Брянская, 16, строение 2</p> 
        </div>
      </div>
    </nav>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      activeIndex: null,
      activeHeight: null
    }
  },
  methods: {
    toggleAccordion(index, event) {
      this.activeHeight = 0
      this.activeIndex = this.activeIndex === index ? null : index
      const parent = event.target.closest('.footer__column')
      const child = parent.querySelector('.footer__column-content')
      this.activeHeight = child.scrollHeight + 37
    }
  }
}
</script>

<style>
  .footer {
    background-color: #38383B;
    padding: 48px 0;
  }

  .footer__menu {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
  }

  .footer__column._big {
    grid-column: span 2;
  }

  .footer__column-name {
    color: #fff;
    font-size: 14px;
    font-weight: bold;
    text-transform: uppercase;
    margin-bottom: 23px;
  }

  .footer__link {
    display: block;
    color: #fff;
    font-size: 14px;
    transition: .2s;
    text-decoration: none;
    width: max-content;
    margin-top: 15px;
  }

  .footer__link:hover {
    color: #FFC72C;
  }

  .footer__link._small {
    margin-top: 2px;
  }

  .footer__item {
    color: #fff;
    margin-top: 15px;
    font-size: 14px;
    line-height: 19px;
  }

  @media (min-width: 769px) {
    .footer__column-content {
      height: 100% !important;
    }
  }

  @media (max-width: 768px) {

    .footer {
      padding: 0 0 24px;
    }
    
    .footer__menu {
      display: block;
      padding: 0;
    }

    .footer__column {
      border-top: 1px solid #898D8D;
      border-bottom: 1px solid #898D8D;
      transition: .2s;
      overflow: hidden;
    }

    .footer__column-name {
      font-size: 16px;
      padding: 15px 12px;
      display: grid;
      grid-template-columns: 1fr auto;
      align-items: center;
      gap: 10px;
      margin: 0;
    }

    .footer__column-name::after {
      content: '';
      display: block;
      width: 10px;
      height: 10px;
      background-image: url('../img/icon-plus.svg');
      background-repeat: no-repeat;
      background-position: center;
      background-size: contain;
    }

    .footer__column-content {
      padding: 0px 12px 0px;
      display: grid;
      gap: 15px;
      height: 0px;
      transition: .2s;
    }

    .footer__link {
      margin: 0;
    }

    .footer__column._open {
      background-color: #2E2E31;
    }

    .footer__column._open .footer__column-content {
      padding: 5px 12px 32px;
    }

    .footer__column._open .footer__column-name::after {
      background-image: url('../img/icon-minus.svg');
    }

    .footer__item {
      margin: 0;
    }
  }
</style>
