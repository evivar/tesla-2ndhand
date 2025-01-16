<template>
  <div class="tsm-select" :class="{ error: isError }">
    <VueSelect
      v-model="selected"
      :options="options"
      :placeholder="placeholder"
      @option-selected="$emit('option-selected', $event)"
      @option-deselected="$emit('option-deselected')"
    />
  </div>
</template>

<script setup>
import VueSelect from "vue3-select-component";
import { ref } from "vue";

defineProps({
  placeholder: {
    type: String,
    default: "Selecciona una opción",
  },
  options: {
    type: Array,
    default: () => [],
  },
  isError: {
    type: Boolean,
    default: false,
  },
});

const selected = ref(null);
</script>

<style lang="scss" scoped>
.tsm-select {
  @apply w-full flex;
  border: 1px solid black;
  border-radius: 10px;
  padding: 8px 16px;
  background: white;
  color: black;
  font-size: 12px;

  &::placeholder {
    color: #9da2cd;
  }
  &:focus,
  &:focus-visible {
    background: white;
    border-color: black;
    outline: none;
  }
}
.error {
  border-color: red;
}

.control {
  border: none !important;
}
</style>

#__nuxt > div > div > div.search--filters > div > div > div
