<template>
  <div class="app-container" :class="{ gridEmpty: cartEmpty }">
    <TheHeader class="header" />
    <Shop class="shop" :products="state.products" @add-product-to-cart="addProductToCart" />
    <Cart
      v-if="!cartEmpty"
      class="cart"
      :cart="state.cart"
      @remove-product-from-cart="removeProductFromCart"
    />
    <TheFooter class="footer" />
  </div>
</template>

<script setup lang="ts">
import TheHeader from '@/components/Layouts/Header/Header.vue'
import TheFooter from '@/components/Layouts/Footer/Footer.vue'
import Shop from '@/components/Shop/Shop.vue'
import Cart from '@/components/Cart/Cart.vue'
import { computed, reactive } from 'vue'
import data from './data/products'
import type { ProductInterface } from './interfaces/Product.interface'
import type { ProductCartInterface } from './interfaces'

const state = reactive<{
  products: ProductInterface[]
  cart: ProductCartInterface[]
}>({
  products: data,
  cart: []
})

const cartEmpty = computed(() => state.cart.length === 0)

const addProductToCart = (productId: number): void => {
  const product = state.products.find((product) => product.id === productId)
  if (product) {
    const productInCart = state.cart.find((product) => product.id === productId)

    if (productInCart) {
      productInCart.quantity++
    } else {
      state.cart.push({ ...product, quantity: 1 })
    }
  }
}

const removeProductFromCart = (productId: number): void => {
  const productFromCart = state.cart.find((product) => product.id === productId)

  if (productFromCart) {
    if (productFromCart.quantity === 1) {
      state.cart = state.cart.filter((product) => product.id !== productId)
    } else {
      productFromCart.quantity--
    }
  }
}
</script>

<style lang="scss">
@import './assets/scss/base.scss';
@import 'assets/scss/debug.scss';

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

.gridEmpty {
  grid-template-areas:
    'header'
    'shop'
    'cart'
    'footer';
  grid-template-columns: 100%;
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
