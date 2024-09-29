<template>
  <div>
    <ShopProductList :products="products" />
  </div>
</template>

<script setup lang="ts">
import ShopProductList from '@/components/Shop/ShopProductList/ShopProductList.vue'
import type { ProductType } from '@/types/Product.type'

defineProps<{
  products: ProductType[]
}>()
</script>

<style lang="scss" scoped></style>
