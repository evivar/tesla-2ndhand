<template>
  <div class="tsm-gallery">
    <Carousel id="gallery" v-bind="galleryConfig" v-model="currentSlide">
      <Slide v-for="image in images" :key="image">
        <div class="carousel__item">
          <img :src="image" alt="Gallery Image" class="gallery-image" />
        </div>
      </Slide>
    </Carousel>

    <Carousel id="thumbnails" v-bind="thumbnailsConfig" v-model="currentSlide">
      <Slide v-for="image in images" :key="image">
        <div class="carousel__item" @click="slideTo(image - 1)">
          <img :src="image" alt="Thumbnail Image" class="thumbnail-image" />
        </div>
      </Slide>

      <template #addons>
        <Navigation />
      </template>
    </Carousel>
  </div>
</template>

<script setup>
import "vue3-carousel/carousel.css";
import { Carousel, Slide, Navigation } from "vue3-carousel";
import { ref } from "vue";

defineProps({
  images: {
    type: Array,
    default: () => [],
  },
});

const currentSlide = ref(0);

const slideTo = (nextSlide) => (currentSlide.value = nextSlide);

const galleryConfig = {
  itemsToShow: 1,
  wrapAround: true,
  slideEffect: "fade",
  mouseDrag: false,
  touchDrag: false,
};

const thumbnailsConfig = {
  itemsToShow: 3.5,
  wrapAround: true,
  gap: 10,
};

const images1 = Array.from({ length: 5 }, (_, index) => ({
  id: index + 1,
  url: `https://picsum.photos/800/600?random=${index + 1}`,
}));
</script>

<style lang="scss" scoped>
.tsm-gallery {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  height: 100%;
}

.gallery-image {
    @apply rounded-ss-lg lg:rounded-se-none rounded-se-lg;
    // border-top-left-radius: 10px;
}
</style>
