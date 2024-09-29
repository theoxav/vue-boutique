<template>
  <div class="app-container">
    <TheHeader class="header" />
    <Shop class="shop" :products="state.products" @add-product-to-cart="addProductToCart" />
    <Cart class="cart" :cart="state.cart" @remove-product-from-cart="removeProductFromCart" />
    <TheFooter class="footer" />
  </div>
</template>

<script setup lang="ts">
import TheHeader from '@/components/Layouts/Header/Header.vue'
import TheFooter from '@/components/Layouts/Footer/Footer.vue'
import Shop from '@/components/Shop/Shop.vue'
import Cart from '@/components/Cart/Cart.vue'
import { reactive } from 'vue'
import data from './data/products'
import type { ProductType } from './types/Product.type'

const state = reactive<{
  products: ProductType[]
  cart: ProductType[]
}>({
  products: data,
  cart: []
})

const addProductToCart = (productId: number): void => {
  const product = state.products.find((product) => product.id === productId)
  if (product && !state.cart.find((product) => product.id === productId)) {
    state.cart.push({ ...product })
  }
}

const removeProductFromCart = (productId: number): void => {
  console.log('in remove')

  state.cart = state.cart.filter((product) => product.id !== productId)
}
</script>

<style lang="scss">
@import './assets/base.scss';
@import 'assets/debug.scss';

.app-container {
  min-height: 100vh;
  display: grid;
  grid-template-areas: 'header header' 'shop cart' 'footer footer';
  grid-template-columns: 75% 25%;
  grid-template-rows: 48px auto 48px;

  @media (max-width: 992px) {
    grid-template-columns: 65% 35%;
  }

  @media (max-width: 768px) {
    grid-template-areas:
      'header'
      'shop'
      'cart'
      'footer';
    grid-template-columns: 100%;
    grid-template-rows: 48px auto auto 48px;
  }
}

.header {
  grid-area: header;
}

.shop {
  grid-area: shop;
}

.cart {
  grid-area: cart;
  border-left: var(--border);
  background-color: white;
}

.footer {
  grid-area: footer;
}
</style>
