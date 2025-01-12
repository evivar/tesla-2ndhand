<template>
  <div class="index">
    <div class="last-added">
      <div class="header">
        <img
          src="@/assets/images/teslaheader.png"
          alt="TeslaSegundaMano"
          class="header--img"
        />
        <TSMSearchWidget />
      </div>
      <div class="content">
        <div class="models">
          <h2 class="title">Modelos</h2>

          <div class="models--items">
            <button class="model--item__btn model-s"><span>Model S</span></button>
            <button class="model--item__btn model-3"><span>Model 3</span></button>
            <button class="model--item__btn model-x"><span>Model X</span></button>
            <button class="model--item__btn model-y"><span>Model Y</span></button>
            <button class="model--item__btn cybertruck lg:col-span-2">
              <span>Cybertruck</span>
            </button>
          </div>
        </div>
        <div class="last">
          <h2 class="title">Últimos anuncios</h2>
          <div class="last--ads">
            <TSMCard v-for="(i, idx) in 4" :key="idx" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import TSMCard from "~/components/atoms/TSMCard.vue";
import TSMSearchWidget from "~/components/molecules/TSMSearchWidget.vue";
</script>

<style lang="scss" scoped>
.index {
  @apply flex flex-col items-center gap-4;
  padding: 1rem;
  max-width: 950px;
  & > .last-added {
    background-color: white;
    border-radius: 10px;
    & > .header {
      position: relative;
      & > img {
        border-top-right-radius: 10px;
        border-top-left-radius: 10px;
      }
      margin-bottom: 1rem;
    }
    & > .content {
      @apply lg:mt-0 mt-[38px];
      padding: 16px;
      display: flex;
      flex-direction: column;
      gap: 1rem;
      & > .models {
        & > .title {
          @apply font-semibold text-center text-lg mb-2;
        }
        & > .models--items {
          @apply grid lg:grid-cols-2 grid-cols-1 gap-4;
          & > .model--item__btn {
            @apply shadow-lg text-2xl font-semibold;
            border-radius: 10px;
            height: 164px;
            background-size: cover;
            background-position: center;
            color: white;
            opacity: 0.75;
            &:hover{
              opacity:1;
            }
            & > span {
              padding: 1rem;
              background: rgba(0, 2, 20, 0.5);
              border-radius: 10px;
            }
          }
        }
      }
      & > .last {
        & > .title {
          @apply font-semibold text-center text-lg mb-2;
        }
        & > .last--ads {
          @apply grid lg:grid-cols-4 grid-cols-2 gap-4;
        }
      }
    }
  }
}

.model-s {
  background-image: url("@/assets/images/model-s.jpg");
}

.model-3 {
  background-image: url("@/assets/images/model-3.jpg");
}
.model-x {
  background-image: url("@/assets/images/model-x.jpg");
}
.model-y {
  background-image: url("@/assets/images/model-y.jpg");
}
.cybertruck {
  background-image: url("@/assets/images/cybertruck.jpg");
}
</style>
