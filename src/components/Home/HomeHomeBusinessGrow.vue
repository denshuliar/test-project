<template>
  <div class="HomeHomeBusinessGrow__wrapper">
    <div v-for="item in growStatData" :key="item.id" class="HomeHomeBusinessGrow__item">
      <div class="HomeHomeBusinessGrow__bg"/>

      <div class="HomeHomeBusinessGrow__text">
        <p>{{ item.text }}</p>
        <span>{{ item.value }}</span>
      </div>
    </div>
  </div>
</template>

<script lang="js">
import {
  ref,
  onMounted
} from 'vue'
import gsap from 'gsap'

export default {
  name: 'HomeHomeBusinessGrow',

  setup () {
    const growStatData = ref([
      {id: 1, text: 'Revenue generated for clients', value: '1570'},
      {id: 2, text: 'Conversation opened', value: '1200'},
      {id: 3, text: 'Leads generated via targeted', value: '378'},
      {id: 4, text: 'Calls scheduled for clients', value: '197'},
    ]);
    
    onMounted(() => {
      gsap.utils.toArray('.HomeHomeBusinessGrow__bg').forEach((item, index) => {
        gsap.fromTo(item,
        { right: '100%' },
        {
          right: 0,
          duration: 0.4,
          delay: index * 0.1,
          scrollTrigger: {
            trigger: item,
            start: "center bottom-=10",
            toggleActions: "play none none none",
          }
        })
      })

      gsap.utils.toArray('.HomeHomeBusinessGrow__item').forEach((item) => {
        gsap.fromTo(item,
        { opacity: 0 },
        {
          opacity: 1,
          duration: 0.5,
          delay: 0.3,
          scrollTrigger: {
            trigger: item,
            start: "center bottom-=10",
            toggleActions: "play none none none",
          }
        })
      })
    })

    return {
      growStatData
    }
  }
}

</script>

<style lang="scss" scoped>
  .HomeHomeBusinessGrow {
    &__wrapper {
      display: flex;
      align-items: flex-end;
      flex-direction: column;
      background-color: $white;
      margin-bottom: 107px;
    }

    &__item {
      position: relative;
      display: flex;
      align-items: center;
      font-size: 22px;
      color: $red;
      padding: 5px 20px;

      > * {
        z-index: 2;
      }

      &:first-of-type{
        justify-content: flex-end;
        width: 100%;
        padding-right: 42px;

        p {
          max-width: 199px;
        }
      }

      &:nth-of-type(2){
        width: 60%;
        padding-left: 148px;

        p {
          max-width: 149px;
        }
      }

      &:nth-of-type(3) {
        width: 100%;
        padding-left: 119px;

        p {
          max-width: 172px;
        }
      }

      &:last-of-type{
        width: 40%;
        padding-left: 170px;

        p {
          max-width: 162px;
        }
      }
    }

    &__text {
      span {
        font-size: 65px;
        font-weight: 400;
      }

      p {
        color: $red;
        text-align: right;
        margin-right: 20px;
        margin-bottom: 0;
        margin-top: -10px;
        line-height: 1.2;
      }
    }

    &__bg {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      z-index: 1;
      background-color: $color-primary;
    }

    &__text {
      width: auto;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
  }
</style>