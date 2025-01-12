<script lang="ts" setup>
import type { Composer } from '~/types/composer';

const epochs = [
  "Medieval",
  "Renaissance",
  "Baroque",
  "Classical",
  "Early Romantic",
  "Romantic",
  "Late Romantic",
  "20th Century",
  "Post-War",
  "21st Century",
]
const epochComposersData = ref<Record<string, Composer[]>>({});
epochs.forEach(async (epoch) => {
  const { data: composers } = await useFetch<{composers: Composer[]}>(`https://api.openopus.org/composer/list/epoch/${epoch}.json`);
  epochComposersData.value[epoch] = composers;
});
</script>

<template>
  <div>
    <template v-for="epoch in epochs" :key="epoch">
      <UDivider :label="epoch" />
      <div class="relative flex flex-col gap-y-4 items-start">
        <template v-for="composer in epochComposersData[epoch]?.composers ?? []" :key="composer.id" >
          <div>
            <NuxtLink :to="`/works/${composer.id}`">
              <div class="flex flex-row items-center gap-x-4">
                <UAvatar
                  :src="composer.portrait"
                  size="2xl"
                  alt="Avatar"
                />
                {{ composer.complete_name }}
              </div>
            </NuxtLink>
          </div>
        </template>
      </div>
    </template>
  </div>
</template>

