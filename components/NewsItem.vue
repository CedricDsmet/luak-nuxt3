<script setup lang="ts">
import type { NewsContent } from "~/types/content.types";

defineProps<{
  data: NewsContent;
  reversed?: boolean;
}>();
</script>

<template>
  <div class="bg-base-100 my-5">
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
        <ContentRenderer
          :value="data"
          :excerpt="true"
          class="py-6 nuxt-content"
        >
          <template #empty>
            <p>Press the read more button to lean more!.</p>
          </template>
          <template #error>
            <p>An error occurred while rendering the content.</p>
          </template>
        </ContentRenderer>
        <NuxtLink :key="data._path" :to="data._path" class="btn btn-outline"
          >read more</NuxtLink
        >
      </div>
    </div>
  </div>
  <div class="divider my-5 mx-20" />
</template>
