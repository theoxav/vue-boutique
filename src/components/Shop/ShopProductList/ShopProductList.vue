<template>
  <div class="grid p-20">
    <ShopProductItem v-for="product of products" :key="product.id" :product="product" />
  </div>
</template>

<script setup lang="ts">
import ShopProductItem from '@/components/Shop/ShopProductItem/ShopProductItem.vue'
import type { ProductType } from '@/types/Product.type'

defineProps<{
  products: ProductType[]
}>()
</script>

<style lang="scss" scoped>
@import './ShopProductList.scss';
</style>
