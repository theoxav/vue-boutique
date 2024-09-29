<template>
  <div>
    <ShopProductList
      :products="products"
      @add-product-to-cart="emit('add-product-to-cart', $event)"
    />
  </div>
</template>

<script setup lang="ts">
import ShopProductList from '@/components/Shop/ShopProductList/ShopProductList.vue'
import type { ProductType } from '@/types/Product.type'

defineProps<{
  products: ProductType[]
}>()

const emit = defineEmits<{
  (event: 'add-product-to-cart', productId: number): void
}>()
</script>

<style lang="scss" scoped></style>
