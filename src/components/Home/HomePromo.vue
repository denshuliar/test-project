<template>
  <section id="promo-section" class="HomePromo">
    <div class="HomePromo__overlay" />

    <div class="HomePromo__wrapper">
      <div class="swiper-wrap">
        <swiper
            :effect="'fade'"
            :modules="modules"
            class="mySwiper"
            :autoplay="{
              delay: 500,
              disableOnInteraction: false
            }"
        >
          <swiper-slide
            v-for="(_banner, id) in 4"
            :key="id + 1"
          >
            <img
              :src="(`/images/0${id + 1}header.png`).replace(/\.jpg$|\.jpeg$|\.png$/, '.webp')"
              :data-backup-src="`images/0${id + 1}header.png`"
              alt="Header banner slide"
              class="HomePromo__banner"
              aria-hidden="true"
              @error="replaceBannerWebp(e)"
            >
          </swiper-slide>
        </swiper>

        <p class="HomePromo__text">Digital Marketing Agency</p>
      </div>
    </div>
  </section>
</template>

<script lang="js">
import { Swiper, SwiperSlide } from 'swiper/vue'
import SwiperCore, { EffectFade, Autoplay } from 'swiper'
import 'swiper/swiper-bundle.css'

import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'

import {
  onMounted
} from 'vue'

SwiperCore.use([EffectFade, Autoplay])

export default {
  name: 'HomePromo',

  components: {
    Swiper,
    SwiperSlide,
  },

  setup() {
    gsap.registerPlugin(ScrollTrigger)

    onMounted(() => {
      gsap.to('.overlay', {
        scrollTrigger: {
          trigger: '#marketing-section',
          start: 'top bottom',
          end: 'bottom center',
          scrub: true,
        },
        opacity: 1,
      })
    })

    const replaceBannerWebp = (e) => {
      e.target.onerror = null
      e.target.src = e.target.getAttribute('data-backup-src')
    }

    return {
      replaceBannerWebp,
      modules: [EffectFade, Autoplay],
    }
  }
}
</script>

<style lang="scss" scoped>
  .HomePromo {
    &__banner {
      height: calc(100vh - 80px);
      background-size: cover;
      background-position: 50% 50%;
      z-index: 1;
    }

    &__overlay {
      display: block;
      position: absolute;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;
      background-color: $color-primary;
      z-index: 2;
      opacity: 0;
    }

    &__text {
      position: absolute;
      text-shadow: 0 4px 4px rgba(0, 0, 0, 0.25);
      color: $red;
      z-index: 9;
      max-width: 140px;
      font-size: 18px;
      top: 20px;
      right: 20px;
    }
  }
</style>
