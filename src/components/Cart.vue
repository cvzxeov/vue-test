<template>
    <div>
      <h1>Корзина</h1>
  
      <!-- Проверка на наличие товаров в корзине -->
      <ul v-if="cartItems.length > 0">
        <li v-for="item in cartItems" :key="item.id">
          {{ item.name }} - {{ item.price }} руб.
        </li>
      </ul>
  
      <!-- Сообщение, если корзина пуста -->
      <p v-else>Корзина пуста.</p>
  
      <!-- Отображение итоговой стоимости и кнопки оформления заказа -->
      <p v-if="totalPrice > 0">Итоговая стоимость: {{ totalPrice }} руб.</p>
  
      <!-- Кнопка оформления заказа только если есть товары в корзине -->
      <button @click="checkout" v-if="cartItems.length > 0">Оформить заказ</button> 
    </div>
  </template>
  
  <script>
  // Компонент для отображения корзины
  export default {
    props: ['cartItems'],
    
    computed: {
      totalPrice() {
        return this.cartItems.reduce((total, item) => total + item.price, 0);
      }
    },
    
    methods: {
      checkout() {
        alert('Заказ оформлен!');
      }
    }
  };
  </script>
  
  <style scoped></style>