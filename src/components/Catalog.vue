<template>
    <div>
      <h1>Каталог товаров</h1>
      <div class="product-card" v-for="product in products" :key="product.id">
        <h2>{{ product.name }}</h2>
        <p>Цена: {{ product.price }} руб.</p>
        <button @click="addToCart(product)">Добавить в корзину</button> <!-- добавление товара в корзину -->
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        products: [
          { id: 1, name: 'Инвокер', price: 100 },
          { id: 2, name: 'Марс', price: 200 },
          { id: 3, name: 'Брюмастер', price: 300 }
        ]
      };
    },
    methods: {
      addToCart(product) {
        this.$emit('add-to-cart', product); // событие для добавления в корзину
      }
    }
  };
  </script>
  
  <style scoped>
  .product-card {
    border: 1px solid #ccc;
    padding: 10px;
    margin: 10px;
  }
  </style>