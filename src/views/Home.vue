<template>
  <div class="container">
    <AppLoader @startMainLogoAnimation="startMainLogoAnimation"/>
    <AppLogo ref="logoRef"/>
    <HomePromoSection />
    <HomeMarketingSection ref="marketing" />
    <HomeBusinessSection />
  </div>
</template>

<script lang="js">
import { gsap } from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'
import ScrollToPlugin from 'gsap/ScrollToPlugin'

import AppLogo from '../components/App/AppLogo.vue'
import AppLoader from '../components/App/AppLoader.vue'
import HomePromoSection from '../components/Home/HomePromo.vue'
import HomeMarketingSection from '../components/Home/HomeMarketing.vue'
import HomeBusinessSection from '../components/Home/HomeBusiness.vue'

import {
  ref,
  onMounted,
} from 'vue'

export default  {
  name: 'Home',

  components: {
    AppLogo,
    AppLoader,
    HomePromoSection,
    HomeMarketingSection,
    HomeBusinessSection
  },

  setup () {
    const logoRef = ref(null)
    const marketing = ref(null)
    
    gsap.registerPlugin(ScrollTrigger)
    gsap.registerPlugin(ScrollToPlugin)
    
    gsap.config({
      nullTargetWarn: false,
      trialWarn: false,
    });


    onMounted(() => {
      gsap.to(window, { duration: 1, scrollTo: 0 })

      gsap.utils.toArray('#promo-section').forEach(section => {
        ScrollTrigger.create({
          trigger: section,
          start: 'top top',
          pin: true,
          pinSpacing: false,
          scrub: 1,
        })
      })

    })
    
    const startMainLogoAnimation = () => {
      logoRef.value.startAnimation()
    }

    return {
      marketing,
      logoRef,
      startMainLogoAnimation,
    }
  }
}
</script>
