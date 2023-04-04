<script setup lang="ts">
const { params } = useRoute();
const client = useMedusaClient();
const { product } = await client.products.retrieve(params.id as string);
</script>

<template>
  <div class="grid grid-cols-2 items-center px-20">
    <NuxtImg
      :src="product.images[0].url"
      class="rounded-lg shadow-lg -rotate-6 w-full"
      alt="Product Image"
      format="webp"
    />
    <div class="rounded-lg shadow-lg p-12 backdrop-blur-2xl">
      <h2 class="text-4xl font-bold mb-6">{{ product.title }}</h2>
      <p class="text-gray-500 mb-6">
        {{ product.description }}
      </p>

      <Button :label="`Pay ${product.variants[0].prices[0].amount}`" icon="pi pi-check"/>
</div>
  </div>
</template>
