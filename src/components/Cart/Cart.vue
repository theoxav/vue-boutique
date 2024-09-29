<template>
  <div class="p-20">
    <h2 class="mb-10">Panier</h2>
    <CartProductList
      :cart="cart"
      @remove-product-from-cart="emit('remove-product-from-cart', $event)"
    />
  </div>
</template>

<script setup lang="ts">
import CartProductList from '@/components/Cart/CartProductList/CartProductList.vue'
import type { ProductType } from '@/types/Product.type'

const props = defineProps<{
  cart: ProductType[]
}>()

const emit = defineEmits<{
  (event: 'remove-product-from-cart', productId: number): void
}>()
</script>

<style lang="scss" scoped></style>
