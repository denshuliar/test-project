<template>
  <section id="business-section" class="HomeBusiness">
    <div class="HomeBusiness__wrapper">
      <div class="HomeBusiness__title">
        <h2>
          <AppAnimatedText text="Growing businesses by building relationships" relatedSection="business" />
        </h2>
      </div>

      <div class="HomeBusiness__text">
        <p>We combine disruptive marketing techniques with proven tech solutions to provide maximum business value.</p>
      </div>
    </div>

    <HomeBusinessCharts :data="chartsData" />
    <HomeHomeBusinessGrow />
  </section>
</template>

<script lang="js">
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'

import {
  ref,
  onMounted
} from 'vue'

import AppAnimatedText from "../App/AppAnimatedText.vue"
import HomeBusinessCharts from "./HomeBusinessCharts.vue"
import HomeHomeBusinessGrow from "./HomeHomeBusinessGrow.vue"

export default {
  name: 'HomeBusiness',

  components: {
    AppAnimatedText,
    HomeBusinessCharts,
    HomeHomeBusinessGrow
  },

  setup () {
    const chartsData = ref([
      {id: 1, value: '27'},
      {id: 2, value: '53'},
      {id: 3, value: '61'},
      {id: 4, value: '58'},
      {id: 5, value: '30'},
      {id: 6, value: '63'},
      {id: 7, value: '55'},
      {id: 8, value: '65'},
      {id: 9, value: '71'},
      {id: 10, value: '76'},
      {id: 11, value: '67'},
      {id: 12, value: '88'},
      {id: 13, value: '78'},
      {id: 14, value: '90'}
    ])
    
    onMounted(() => {
      gsap.registerPlugin(ScrollTrigger)

      ScrollTrigger.create({
        trigger: '#business-section',
        start: 'bottom 50%',
        onEnter: () => {
          gsap.to(window, { delay: 1, duration: 1, scrollTo: '#business-section' })
        },
      })

      gsap.utils.toArray('.HomeBusinessCharts__item').forEach((item, index) => {
        gsap.fromTo(item,
          { height: 0 },
          {
            height: chartsData.value[index].value + '%',
            duration: 0.5,
            delay: 0.2 + chartsData.value[index].id * 0.1,
            scrollTrigger: {
              trigger: '.HomeBusinessCharts__wrapper',
              start: "center bottom-=100",
              toggleActions: "play none none none",
            }
          })
      })
    })

    return {
      chartsData
    }
  }
}

</script>

<style lang="scss" scoped>
  .HomeBusiness {
    background-color: $white;
    position: relative;
    display: flex;
    flex-direction: column;
    z-index: 1;
    height: 100%;
    padding-top: 30px;

    &__wrapper {
      padding: 20px;
    }

    &__title {
      min-height: 175px;
      max-width: 1282px;

      h2 {
        margin-bottom: 0;
        line-height: 1;
        font-weight: 400;
        width: 100%;
        font-size: 55px;
        font-size: 82px;
      }
    }

    &__text {
      margin-top: 60px;
      font-size: 22px;
      max-width: 580px;
    }
  }
</style>