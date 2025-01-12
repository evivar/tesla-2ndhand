<template>
  <div class="car">
    <div class="content">
      <div class="photos"><TSMGallery /></div>
      <div class="info">
        <div class="info--content">
          <h1 class="name">Tesla Model X</h1>
          <h2 class="city">Murcia</h2>
          <div class="specs">
            <div class="specs--row">
              <div class="specs--row__item">
                <img src="@/assets/images/t-year.svg" alt="Year" />
                <span class="year">2025</span>
              </div>
              <div class="specs--row__item border-x">
                <img src="@/assets/images/t-model.svg" alt="Model" />
                <span class="model">Model X</span>
              </div>
              <div class="specs--row__item">
                <img src="@/assets/images/t-kms.png" alt="Kms" width="32px" />
                <span class="kms">75.000 kms</span>
              </div>
            </div>
            <div class="specs--row border-y">
              <div class="specs--row__item">
                <img src="@/assets/images/t-shift.svg" alt="Kms" />
                <div class="shift">Automatico</div>
              </div>
              <div class="specs--row__item border-x">
                <img src="@/assets/images/t-oil.svg" alt="Kms" />
                <div class="oil">Eléctrico</div>
              </div>
              <div class="specs--row__item">
                <img src="@/assets/images/t-cv.svg" alt="Kms" />
                <div class="ccv">200 cv</div>
              </div>
            </div>
            <div class="specs--row">
              <div class="specs--row__item">
                <img src="@/assets/images/t-color.svg" alt="Kms" />
                <div class="color">Verde</div>
              </div>
              <div class="specs--row__item border-x">
                <img src="@/assets/images/t-door.svg" alt="Kms" />
                <div class="doors">5 puertas</div>
              </div>
              <div class="specs--row__item">
                <img src="@/assets/images/t-seat.svg" alt="Kms" />
                <div class="seats">5 plazas</div>
              </div>
            </div>
          </div>
          <p class="description">
            Vendo Tesla Model X 2024, impecable, con solo 75.000 km. Autonomía superior,
            diseño elegante y tecnología de vanguardia. Cuidado al detalle, listo para
            disfrutar. ¡No dejes pasar esta oportunidad!
          </p>
        </div>
        <div class="info--price">
          <span>150.000€</span>
        </div>
      </div>
    </div>
    <div class="contact">
      <span class="title"> Contacto </span>
      <div class="content">
        <div class="content--user">
          <img src="@/assets/images/t-userplaceholder.svg" alt="User" width="48px" />
          <span class="name">Benito Kamelas</span>
          <span class="city">Murcia</span>
        </div>
        <div class="content--links">
          <span class="link"> Enviar Mail </span>
          <span class="link" @click="sendWhatsapp"> Enviar Whatsapp </span>
          <span class="link"> Llamar </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive } from "vue";
import { useRouter, useRoute } from "vue-router";
import TSMGallery from "~/components/organisms/TSMGallery.vue";

const route = useRoute();
const router = useRouter();

// TODO: Ponerlo en un .env
const whatsappModel = reactive({
  phoneNumber: "34651408843",
  message: `Hola, estoy usando el modelo Tesla Model X 2024\n${window.location.href}`,
});

const sendWhatsapp = () => {
  console.log("router :>> ", router);
  console.log("route :>> ", route);
  const encodedMessage = encodeURIComponent(whatsappModel.message);
  const whatsappUrl = `https://wa.me/${whatsappModel.phoneNumber}?text=${encodedMessage}`;
  window.open(whatsappUrl, "_blank");
};
</script>

<style lang="scss" scoped>
.car {
  @apply flex flex-col items-center gap-4 w-full;
  padding: 1rem;
  max-width: 950px;
  & > .content {
    @apply grid lg:grid-cols-2 grid-cols-1 gap-4;
    background-color: white;
    border-radius: 10px;
    width: 100%;
    & > .images {
      @apply lg:max-w-[40%] w-full;
    }
    & > .info {
      @apply flex flex-col gap-4;
      padding: 1rem;
      & > .info--content {
        @apply flex flex-col gap-1;
        & > .name {
          @apply font-semibold lg:text-lg text-base;
        }
        & > .city {
          @apply text-sm font-light;
        }
      }
      & > .info--price {
        @apply font-semibold text-lg;
      }
    }
  }
  & > .contact {
    background-color: white;
    border-radius: 10px;
    width: 100%;
    padding: 1rem;
    & > .title {
      @apply font-semibold lg:text-lg text-base;
    }
    & > .content {
      @apply lg:flex-row flex-col gap-2;
      display: flex;
      flex-wrap: nowrap;
      justify-content: space-between;
      align-items: center;

      & > .content--user {
        @apply flex flex-col gap-1;
      }
      & > .content--links {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 0.5rem;
        & > .link {
          @apply font-semibold shadow-sm w-full text-center;
          cursor: pointer;
          background: #000214;
          color: white;
          padding: 0.5rem 1rem;
          border-radius: 60px;
          &:hover {
            @apply shadow-lg;
          }
        }
      }
    }
  }
}

.specs {
  margin-top: 1rem;
  margin-bottom: 1rem;
  display: grid;
  grid-template-rows: 1fr 1fr 1fr;
  &--row {
    display: grid;
    align-items: center;
    justify-content: space-between;
    grid-template-columns: 1fr 1fr 1fr;
    padding: 4px;
    &__item {
      @apply text-center text-sm;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
  }
}
</style>
