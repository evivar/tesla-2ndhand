<template>
  <div class="tsm-search-widget">
    <div class="title">
      <span>logo </span>
      <span>Encuentra tu próximo Tesla</span>
    </div>
    <div class="content">
      <TSMInput placeholder="Busca tu Tesla" />
      <div class="content--row">
        <TSMInput placeholder="Provincia" />
        <TSMInput placeholder="Precio" />
      </div>
    </div>
  </div>
</template>

<script setup>
import TSMInput from "../atoms/TSMInput.vue";
</script>

<style lang="scss" scoped>
.tsm-search-widget {
  @apply lg:flex shadow-md lg:translate-y-1/2 translate-y-1/3 flex-col gap-4;
  background-color: rgba(0, 2, 20, 0.5);
  border-radius: 10px;
  max-width: 350px;
  position: absolute;
  right: 1.5rem;
  top: 20%;
  width: 100%;
  padding: 0.5rem;
  @media (width < 425px) {
    right: 0;
  }
  & > .title {
    @apply font-semibold flex flex-row justify-between items-center mb-2;
    color: white;
  }
  & > .content {
    @apply flex flex-col gap-2 w-full;
    & > .content--row {
      @apply w-full flex flex-row gap-2;
    }
  }
}
</style>
