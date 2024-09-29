<template>
  <div class="grid p-20">
    <ShopProductItem
      v-for="product of products"
      :key="product.id"
      :product="product"
      @add-product-to-cart="emit('add-product-to-cart', $event)"
    />
  </div>
</template>

<script setup lang="ts">
import ShopProductItem from '@/components/Shop/ShopProductItem/ShopProductItem.vue'
import type { ProductType } from '@/types/Product.type'

defineProps<{
  products: ProductType[]
}>()

const emit = defineEmits<{
  (event: 'add-product-to-cart', productId: number): void
}>()
</script>

<style lang="scss" scoped>
@import './ShopProductList.scss';
</style>
