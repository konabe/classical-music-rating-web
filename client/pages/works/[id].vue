<script lang="ts" setup>
const route = useRoute()
type Work = {id: string; title: string;}
const { data: works } = await useFetch<{works: Work[]}>(`https://api.openopus.org/work/list/composer/${route.params.id}/genre/all.json`);
</script>

<template>
  <div class="relative flex flex-col gap-y-4">
    <template v-for="work in works?.works" :key="work.id">
      <div>
        {{ work.title }}
      </div>
    </template>
  </div>
</template>

