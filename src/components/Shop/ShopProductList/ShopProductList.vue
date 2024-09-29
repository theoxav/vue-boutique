<template>
  <div class="grid p-20">
    <ShopProductItem />
    <ShopProductItem />
    <ShopProductItem />
    <ShopProductItem />
    <ShopProductItem />
    <ShopProductItem />
    <ShopProductItem />
  </div>
</template>

<script setup lang="ts">
import ShopProductItem from '@/components/Shop/ShopProductItem/ShopProductItem.vue'
</script>

<style lang="scss" scoped>
@import './ShopProductList.scss';
</style>
