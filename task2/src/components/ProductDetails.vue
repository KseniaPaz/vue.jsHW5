<template>
    <div>
      Выберите валюту:
      <select size="1" name="" id="" v-model="valuta">
        <option>₽</option>
        <option>€</option>
        <option>$</option>
      </select>
      <br><br><br>
      <div v-for="product in products" :key="product.id">
        <p>Название: {{ product.name }}</p>
        <p>Цена: {{ formattedPrice(product.price) }}</p>
        <p v-if="product.available">Статус: Available</p>
        <p v-else>Статус: Out of stock</p>
        <br>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ProductDetails',
  
    data () {
      return {
        price: '',
        valuta: '',
        products: [
          {
            id: 1,
            name: 'Самокат',
            price: 6000,
            available: true
          },
          {
            id: 2,
            name: 'Велосипед',
            price: 15000,
            available: false
          },
          {
            id: 3,
            name: 'Скейтборд',
            price: 3000,
            available: true
          },
        ]
      };
    },
  
    computed: {
      formattedPrice () {
        if (this.valuta === '₽') {
          return price => `${price} рублей`
        } else if (this.valuta === '€') {
          return price => `€ ${(price / 100.3).toFixed(2)}`;
        } else {
          return price => `$ ${(price / 94.71).toFixed(2)}`
        }
      }
    },
  
    mounted () {
  
    },
  
    methods: {
  
    },
  };
  </script>
  
  <style lang="scss" scoped>
  </style>