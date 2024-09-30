<template>
  <div class="p-20">
    <h2 class="mb-10">Panier</h2>
    <CartProductList
      :cart="cart"
      @remove-product-from-cart="emit('remove-product-from-cart', $event)"
    />
    <button class="btn btn-success">Commander ({{ totalPrice }}€)</button>
  </div>
</template>

<script setup lang="ts">
import CartProductList from '@/components/Cart/CartProductList/CartProductList.vue'
import type { ProductCartInterface } from '@/interfaces'
import { computed } from 'vue'

const props = defineProps<{
  cart: ProductCartInterface[]
}>()

const emit = defineEmits<{
  (event: 'remove-product-from-cart', productId: number): void
}>()

const totalPrice = computed(() =>
  props.cart.reduce((total, product) => total + product.price * product.quantity, 0)
)
</script>

<style lang="scss" scoped></style>
