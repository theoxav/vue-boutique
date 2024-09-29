<template>
  <div class="mb-10 p-10 d-flex flex-row align-items-center product">
    <strong class="flex-fill mr-10">{{ product.title }}</strong>
    <span class="mr-10">Prix : {{ product.price }}€</span>
    <button class="btn btn-danger" @click="emit('remove-product-from-cart', product.id)">
      Supprimer
    </button>
  </div>
</template>

<script setup lang="ts">
import type { ProductType } from '@/types/Product.type'

const props = defineProps<{
  product: ProductType
}>()

const emit = defineEmits<{
  (event: 'remove-product-from-cart', productId: number): void
}>()
</script>

<style lang="scss" scoped>
@import './CartProductItem.scss';
</style>
