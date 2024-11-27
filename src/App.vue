<template>
  <div id="app">
    <header>
      <nav>
        <ul>
          <li style="color: aliceblue;" @click="currentPage = 'home'">Главная</li>
          <li style="color: aliceblue;" @click="currentPage = 'about'">О нас</li>
          <li style="color: aliceblue;" @click="currentPage = 'catalog'">Каталог</li>
          <li style="color: aliceblue;" @click="currentPage = 'cart'">Корзина ({{ cart.length }})</li> <!-- количество товаров в корзине -->
        </ul>
      </nav>
    </header>

    <main>
      <component :is="currentPageComponent" 
                 @add-to-cart="addToCart" 
                 :cartItems="cart"></component> <!-- передаем корзину в компонент -->
    </main>
  </div>
</template>

<script>
import Home from './components/Home.vue';
import About from './components/About.vue';
import Catalog from './components/Catalog.vue';
import Cart from './components/Cart.vue';

export default {
  data() {
    return {
      currentPage: 'home',
      cart: [] // состояние корзины
    };
  },
  computed: {
    currentPageComponent() {
      return {
        home: Home,
        about: About,
        catalog: Catalog,
        cart: Cart
      }[this.currentPage];
    }
  },
  methods: {
    addToCart(product) {
      this.cart.push(product); // добавляем товар в корзину
      alert(`${product.name} добавлен в корзину!`);
    }
  },
};
</script>

<style>
header {
  background-color: #ff0000;
  padding: 10px;
}
nav ul {
  list-style-type: none;
}
nav li {
  display: inline;
  margin-right: 15px;
  cursor: pointer;
}
</style>