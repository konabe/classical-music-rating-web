<template>
  <div class="relative">
    <nav class="fixed top-0 left-0 right-0 bg-gray-800 h-16 pl-8 pr-8 z-10">
      <div class="flex flex-row items-center h-full justify-between">
        <NuxtLink to="/">
          クラシック音楽レビュー
        </NuxtLink>
        <div>
          ログイン
        </div>
      </div>
    </nav>
    <div class="mt-16 p-8">
      <slot />
    </div>
  </div>
</template>
