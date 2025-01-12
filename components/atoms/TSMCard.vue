<template>
  <NuxtLink :to="`/car/1`" class="tsm-card">
    <div class="image">
      <div class="like">
        <span class="material-symbols-outlined"> favorite </span>
      </div>
    </div>
    <div class="content">
      <span class="title">Tesla Model 3</span>
      <div class="flex flex-row gap-2">
        <span class="kms">50.000 kms</span>
        <span>|</span>
        <span class="province">Madrid</span>
      </div>
      <span class="price">100.000€</span>
    </div>
  </NuxtLink>
</template>

<script setup>

</script>

<style lang="scss" scoped>
.tsm-card {
  @apply shadow-lg;
  height: 250px;
  border-radius: 10px;
  background: $light-lilac;
  display: flex;
  flex-direction: column;
  gap: 8px;
  & > .image {
    background-image: url("@/assets/images/model-y.jpg");
    border-top-right-radius: 10px;
    border-top-left-radius: 10px;
    background-size: cover;
    background-position: center;
    height: 50%;
    & > .like {
      cursor: pointer;
      display: flex;
      width: 32px;
      height: 32px;
      border-radius: 50px;
      background: $light-lilac;
      text-align: center;
      align-items: center;
      justify-content: center;
      position: relative;
      left: 80%;
      top: 5%;
    }
  }
  & > .content {
    padding: 8px;
    display: flex;
    flex-direction: column;
    gap: 8px;
    & > .title {
      @apply font-semibold;
    }
    & > .kms {
      @apply text-sm;
    }
    & > .province {
      @apply text-sm;
    }
    & > .price {
      @apply font-semibold;
    }
  }
  &:hover{
    @apply shadow-2xl;
  }
}
</style>
