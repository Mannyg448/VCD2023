<script setup>
  import { ref } from 'vue'
  const pages = ref(10)
  const activePage = ref(4)
  const prevPage = () => {
    if (activePage.value > 1) {
      activePage.value--
    }
  }
  const nextPage = () => {
    if (activePage.value < pages.value) {
      activePage.value++
    }
  }
</script>

<template>
  <div class="pagination">
    <button class="action" :disabled="activePage === 1" @click="prevPage">Prev</button>
    <button class="page" v-for="page in pages" :class="page === activePage ? 'active' : ''" @click="activePage = page">
      {{ page }}
    </button>
    <button class="action" :disabled="activePage === pages" @click="nextPage">Next</button>
  </div>
</template>

<style lang="postcss" scoped>
  .pagination {
    @apply flex justify-center gap-4;
    .action {
      @apply rounded-md bg-green-500 p-2 font-medium text-black shadow-md hover:bg-purple-200 disabled:text-slate-200 hover:disabled:bg-slate-500;
    }
    .page {
      @apply rounded-md bg-slate-100 p-2 font-medium text-slate-700 shadow-md hover:bg-slate-200;
      &.active {
        @apply bg-purple-700 text-slate-100 hover:bg-purple-600;
      }
    }
  }
</style>