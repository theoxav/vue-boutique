<template>
  <div class="product d-flex flex-column p-20">
    <div class="product-image" :style="{ backgroundImage: `url(${product.image})` }"></div>
    <div class="p-10 d-flex flex-column">
      <h4>{{ product.title }}</h4>
      <p>{{ product.description }}</p>
      <div class="d-flex flex-row align-items-center">
        <strong class="flex-fill">Prix : {{ product.price }}€</strong>
        <button class="btn btn-primary" @click="emit('add-product-to-cart', product.id)">
          Ajouter au panier
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import type { ProductType } from '@/types/Product.type'

defineProps<{
  product: ProductType
}>()

const emit = defineEmits<{
  (event: 'add-product-to-cart', productId: number): void
}>()
</script>
<style lang="scss" scoped>
@import './ShopProductItem.scss';
</style>
