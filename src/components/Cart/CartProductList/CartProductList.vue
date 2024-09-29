<template>
  <div class="d-flex flex-column">
    <CartProductItem
      v-for="product of cart"
      :key="product.id"
      :product="product"
      @remove-product-from-cart="emit('remove-product-from-cart', $event)"
    />
  </div>
</template>

<script setup lang="ts">
import CartProductItem from '@/components/Cart/CartProductItem/CartProductItem.vue'
import type { ProductType } from '@/types/Product.type'

const props = defineProps<{
  cart: ProductType[]
}>()

const emit = defineEmits<{
  (event: 'remove-product-from-cart', productId: number): void
}>()
</script>

<style lang="scss" scoped></style>
