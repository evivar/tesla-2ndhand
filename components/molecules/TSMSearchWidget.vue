<template>
  <div class="tsm-search-widget">
    <div class="title">
      <span>logo </span>
      <span>Encuentra tu próximo Tesla</span>
    </div>
    <div class="content">
      <TSMSelect
        :options="modelOptions"
        placeholder="Selecciona un modelo"
        @option-selected="selectedModel = $event.value"
        @option-deselected="selectedModel = null"
      />
      <div class="content--row">
        <TSMSelect
          :options="kmsOptions"
          placeholder="Kms."
          @option-selected="selectedKms = $event.value"
          @option-deselected="selectedKms = null"
        /><TSMSelect
          :options="priceOptions"
          placeholder="Precio"
          @option-selected="selectedPrice = $event.value"
          @option-deselected="selectedPrice = null"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import TSMSelect from "../atoms/TSMSelect.vue";

const modelOptions = ref([
  { value: "Model S", label: "Model S" },
  { value: "Model 3", label: "Model 3" },
  { value: "Model X", label: "Model X" },
  { value: "Model Y", label: "Model Y" },
  { value: "Cybertruck", label: "Cybertruck" },
]);

const priceOptions = ref([]);
const kmsOptions = ref([]);

// Generar opciones de precios
for (let i = 1000; i <= 200000; i += 1000) {
  priceOptions.value.push({
    value: i,
    label: `${i.toLocaleString()} €`, // Formato "1.000 €"
  });
}

// Generar opciones de kilómetros
for (let i = 0; i <= 250000; i += 12500) {
  kmsOptions.value.push({
    value: i,
    label: `${i.toLocaleString()}`, // Formato "12.500 kms"
  });
}

const selectedModel = ref(null);
const selectedKms = ref(null);
const selectedPrice = ref(null);
</script>

<style lang="scss" scoped>
.tsm-search-widget {
  @apply lg:flex shadow-md lg:translate-y-1/2 translate-y-1/3 flex-col gap-4;
  background-color: rgba(0, 2, 20, 0.5);
  border-radius: 10px;
  max-width: 400px;
  position: absolute;
  right: 1.5rem;
  top: 20%;
  width: 100%;
  padding: 0.5rem;
  z-index: 1;
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
