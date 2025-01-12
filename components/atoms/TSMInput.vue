<template>
  <div class="tsm-input " :class="{ error: isError }">
    <input
      :value="modelValue"
      :type="type"
      :placeholder="placeholder"
      name="input"
      @input="$emit('update:modelValue', $event.target.value)"
    />
    <slot name="icon"></slot>
  </div>
</template>

<script setup>
defineProps({
  type: {
    type: String,
    default: "text",
  },
  placeholder: {
    type: String,
    default: null,
  },
  modelValue: {
    type: String,
    default: "",
  },
  isError: {
    type: Boolean,
    default: false,
  },
});
</script>

<style lang="scss" scoped>
.tsm-input   {
  @apply w-full flex;
  height: 38px;
  border: 1px solid black;
  border-radius: 10px;
  padding: 8px 16px;
  background: white;
  color: black;
  font-size: 14px;
  & > input {
    @apply w-full;
    background: white;
    &:focus,
    &:focus-visible {
      border-color: black;
      outline: none;
    }
  }
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
</style>
