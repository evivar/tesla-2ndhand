<template>
  <div class="default-layout">
    <nav class="default-layout--header">
      <nuxt-link to="/"><span>Tesla SegundaMano</span></nuxt-link>

      <div class="default-layout--header__models">
        <span class="model">Model S</span>
        <span class="model">Model 3</span>
        <span class="model">Model X</span>
        <span class="model">Model Y</span>
        <span class="model">Cybertruck</span>
      </div>
      <div class="default-layout--header__user">
        <span>User</span>
      </div>
    </nav>
    <slot id="content" />
    <footer class="default-layout--footer">
     <div class="default-layout--footer__left">Left</div>
     <div class="default-layout--footer__right">Right</div>
    </footer>
  </div>
</template>

<script setup></script>

<style lang="scss" scoped>
.default-layout {
  min-height: 100vh;
  height: 100%;
  background: $light-lilac;
  display: flex;
  flex-direction: column;
  align-items: center;
  &--header {
    @apply h-[64px] flex flex-row items-center justify-between w-full shadow-lg;
    padding: 1rem;
    position: sticky;
    z-index: 5;
    top: 0;
    background: white;
    &__models {
      @apply lg:flex hidden flex-row gap-3;
    }
  }
  &--footer{
    @apply grid lg:grid-cols-2 grid-cols-1 gap-4 mt-auto;
    background: #000214;
    color: white;
    width: 100%;
    padding: 1rem;
    justify-items: center;;
    & > .sitemap{
      @apply flex flex-col gap-2 text-sm;
      &--link > span {
        cursor:pointer;
        &:hover{
          @apply font-semibold;
        }
      }
    }
  }
}

.model {
  cursor: pointer;
  &:hover {
    @apply font-semibold;
  }
}

#content {
    flex-grow: 1; // Permite que el contenido principal ocupe el espacio disponible
    max-width: 950px;
    width: 100%; // Opcional: Asegura que el contenido se estire
  }
</style>
