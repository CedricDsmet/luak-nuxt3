<script setup lang="ts">
defineProps<{
  data: {
    title: string;
    image?: string;
    excerpt: object;
    _path: string;
  };
  reversed?: boolean;
}>();
</script>

<template>
  <div class="bg-base-100 m-5">
    <div
      class="flex justify-center items-center align-middle flex-col"
      :class="[reversed ? 'md:flex-row' : 'md:flex-row-reverse']"
    >
      <NuxtImg
        :src="data.image"
        class="rounded-lg shadow-2xl max-w-72 max-h-72 md:max-w-80 md:max-h-80 m-5"
        :placeholder="384"
      />
      <div>
        <h1 class="text-4xl text-gray-600">{{ data.title }}</h1>
        <ContentRenderer :value="data" :excerpt="true" class="py-6" />
        <span />
        <NuxtLink :key="data._path" :to="data._path" class="btn btn-outline"
          >read more</NuxtLink
        >
      </div>
    </div>
  </div>
  <div class="divider my-5 mx-20" />
</template>
