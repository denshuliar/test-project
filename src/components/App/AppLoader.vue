<template>
  <div v-if="showLoader" class="AppLoader">
    <div class="AppLoader__number">{{ currentNumber }}</div>
  </div>
</template>

<script lang="js">
import gsap from 'gsap'

import {
  ref,
  onMounted
} from 'vue'

export default  {
  name: 'AppLoader',

  setup (_props, { emit }) {
    const numbers = ['02', '06', '12', '24', '48', '56', '64', '76', '82', '98', '100']
    const currentNumber = ref(null)
    const showLoader = ref(true)
    let numberIndex = 0

    const changeNumber = () => {
      numberIndex++;
      if (numberIndex < numbers.length) {
        currentNumber.value = numbers[numberIndex];
      } else {
        currentNumber.value = ''
        animateSectionOne()

        gsap.to('.AppLoader__number', {
          duration: 0.5,
          opacity: 0,
          onComplete: () => {
            setTimeout(hideLoader, 200)
          }
        })
      }
    };

    const animateSectionOne = () => {
      gsap.fromTo("#promo-section", {
        top: 100
      },
      {
        top: 0,
        duration: 1,
        delay: 2
      })

      gsap.fromTo('#marketing-section', {
        top: 80
      },
      {
        top: 0,
        duration: 1,
        delay: 2
      })
    };

    const hideLoader = () => {
      emit('startMainLogoAnimation')

      gsap.to('.AppLoader', {
        duration: 1,
        y: -window.innerHeight,
        delay: 1,
        onComplete: () => {
          showLoader.value = false
          document.body.classList.add('loaded')
        }
      })
    }

    onMounted(() => {
      const interval = setInterval(changeNumber, 300)
      setTimeout(() => {
        clearInterval(interval)
        changeNumber()
      }, numbers.length * 300)
    })

    return {
      showLoader,
      currentNumber
    }
  }
}
</script>

<style scoped lang="scss">
  .AppLoader {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: $color-primary;
    display: flex;
    justify-content: flex-end;
    align-items: flex-end;
    font-size: 100px;
    z-index: 98;

    &__number {
      font-size: 230px;
      color: $red;
      font-weight: 400;
      padding-right: 20px;
      line-height: 1;
    }
  }
</style>
