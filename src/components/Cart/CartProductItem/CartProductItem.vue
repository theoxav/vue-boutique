<template>
  <div class="mb-10 p-10 d-flex flex-row align-items-center product">
    <strong class="flex-fill mr-10">{{ product.title }}</strong>
    <span class="mr-10">Quantite : {{ product.quantity }}</span>
    <span class="mr-10">Prix : {{ product.price }}€</span>
    <button class="btn btn-danger" @click="handleRemove">Supprimer</button>
  </div>
</template>

<script setup lang="ts">
import type { ProductCartInterface } from '@/interfaces'

const props = defineProps<{
  product: ProductCartInterface
}>()

const emit = defineEmits<{
  (event: 'remove-product-from-cart', productId: number): void
}>()

const handleRemove = () => {
  emit('remove-product-from-cart', props.product.id)
}
</script>

<style lang="scss" scoped>
@import './CartProductItem.scss';
</style>
