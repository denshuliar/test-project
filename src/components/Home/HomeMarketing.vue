<template>
  <section id="marketing-section" class="HomeMarketing">
    <HomeMarketingNav />
    
    <div class="HomeMarketing__wrapper">
      <div class="HomeMarketing__title">
        <h2>
          <AppAnimatedText text="Growing businesses by building relationships" relatedSection="marketing" />
        </h2>
      </div>

      <div class="HomeMarketing__text">
        <p>B2B Marketing & LinkedIn Lead Generation agency</p>
      </div>
    </div>
  </section>
</template>

<script lang="js">
  import AppAnimatedText from "../App/AppAnimatedText.vue"
  import HomeMarketingNav from './HomeMarketingNav.vue'

  export default {
    name: 'HomeMarketing',

    components: {
      AppAnimatedText,
      HomeMarketingNav
    }
  }
</script>

<style lang="scss" scoped>
  .HomeMarketing {
    &__wrapper {
      padding: 74px 20px 30px;
      position: relative;
      background-color: $red;
      display: grid;
      min-height: calc(100vh - 80px);
      z-index: 10;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }
  
    &__title {
      display: flex;
      justify-content: flex-end;

      h2 {
        text-align: right;
        font-weight: 400;
        margin: 0;
        max-width: 835px;
        line-height: 1;
        font-size: 135px;
      }
    }
  
    &__text {
      max-width: 318px;
      font-size: 22px;
    }
  }
</style>