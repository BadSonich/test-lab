<template>
  <section v-if="slides.length > 0" class="reviews">
    <div class="container">
      <h2>Отзывы</h2>
      <swiper
          :modules="modules"
          :breakpoints="{
            '0': {
              slidesPerView: 1,
              spaceBetween: 16,
            },
            '568': {
              slidesPerView: 2,
              spaceBetween: 24,
            },
            '768': {
              slidesPerView: 2,
              spaceBetween: 32,
            },
            '992': {
              slidesPerView: 3,
              spaceBetween: 32,
            },
          }"
          navigation
          :pagination="{ clickable: true }"
          @swiper="onSwiper"
          @slideChange="onSlideChange"
      >
        <swiper-slide v-for="(slide, index) in slides" class="reviews__element" :key="index">
          <div>
              <div class="reviews__header">
                <div class="reviews__img">
                  <img :src="slide.img" :alt="'slide' + index">
                </div>
                <div>
                  <h6>{{ slide.name }}</h6>
                  <div class="reviews__city">{{ slide.city }}</div>
                </div>
              </div>
              <p>
                {{ slide.text }}
              </p>
        </div>
        </swiper-slide>
      </swiper>
    </div>
  </section>
</template>
<script>
  import { Navigation, Pagination } from 'swiper/modules';
  import { Swiper, SwiperSlide } from 'swiper/vue';

  import 'swiper/css';
  // import 'swiper/css/navigation';
  import 'swiper/css/pagination';

  export default {
    name: "site-reviews",
    components: {
      Swiper,
      SwiperSlide,
    },
    data() {
      return {
        slides: [
          {
            img: "/reviews/088d382ed0b689cf96b415edbf92f1b3.jpeg",
            name: "Константинов Михаил Павлович",
            city: "Санкт-Петербург",
            text: "Каждый из нас понимает очевидную вещь: перспективное планирование предоставляет широкие возможности для анализа существующих паттернов поведения. В своём стремлении улучшить пользовательский опыт мы"
          },
          {
            img: "/reviews/db5f1aa6994f0a3a6a7e19557191c7d9.png",
            name: "Иван Иванов",
            city: "Санкт-Петербург",
            text: "Каждый из нас понимает очевидную вещь: перспективное планирование предоставляет широкие возможности для анализа существующих паттернов поведения. В своём стремлении улучшить пользовательский опыт мы упускаем, что активно развивающиеся страны третьего мира призваны к ответу."
          },
          {
            img: "/reviews/ad8622a80fadc9dc9dc3f30e3e065f14.png",
            name: "Артем Корнилов",
            city: "Самара",
            text: "Каждый из нас понимает очевидную вещь: перспективное планирование предоставляет широкие возможности для анализа существующих паттернов поведения."
          },
          {
            img: "/reviews/088d382ed0b689cf96b415edbf92f1b3.jpeg",
            name: "Константинов Михаил Павлович",
            city: "Санкт-Петербург",
            text: "Каждый из нас понимает очевидную вещь: перспективное планирование предоставляет широкие возможности для анализа существующих паттернов поведения. В своём стремлении улучшить пользовательский опыт мы"
          },
          {
            img: "/reviews/db5f1aa6994f0a3a6a7e19557191c7d9.png",
            name: "Иван Иванов",
            city: "Санкт-Петербург",
            text: "Каждый из нас понимает очевидную вещь: перспективное планирование предоставляет широкие возможности для анализа существующих паттернов поведения. В своём стремлении улучшить пользовательский опыт мы упускаем, что активно развивающиеся страны третьего мира призваны к ответу."
          },
          {
            img: "/reviews/ad8622a80fadc9dc9dc3f30e3e065f14.png",
            name: "Артем Корнилов",
            city: "Самара",
            text: "Каждый из нас понимает очевидную вещь: перспективное планирование предоставляет широкие возможности для анализа существующих паттернов поведения."
          },
        ],
      }
    },
    setup() {
      const onSwiper = (swiper) => {
        console.log(swiper);
      };
      const onSlideChange = () => {
        console.log('slide change');
      };
      return {
        onSwiper,
        onSlideChange,
        modules: [Navigation, Pagination]
      };
    },
  };
</script>