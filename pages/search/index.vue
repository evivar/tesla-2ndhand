<template>
  <div class="search">
    <div class="search--filters">
        <span class="title">Filtros</span>
        <TSMSelect/>
    </div>
    <div class="search--results">
        <span class="title">Resultados</span>
        <div class="content">
            <TSMCard v-for="(i, idx) in 17" :key="idx" />
        </div>
    </div>
  </div>
</template>

<script setup>
import TSMCard from '~/components/atoms/TSMCard.vue';
import TSMSelect from '~/components/atoms/TSMSelect.vue';
</script>

<style lang="scss" scoped>
.search {
  @apply flex flex-col items-center gap-4;
  padding: 1rem;
  max-width: 950px;
  width: 100%;
  &--filters{
    padding: 1rem;
    width: 100%;
    background-color: white;
    border-radius: 10px;
    & > .title{
      @apply font-semibold text-lg;
    }
  }
  &--results{
    padding: 1rem;
    width: 100%;
    background-color: white;
    border-radius: 10px;
    & > .title{
      @apply font-semibold text-lg;
    }
    & > .content{
      @apply grid lg:grid-cols-4 grid-cols-2 gap-4 mt-4;
    }
  }
}
</style>
