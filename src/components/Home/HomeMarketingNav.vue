<template>
  <div class="HomeMarketingNav">
    <router-link to='/' class="HomeMarketingNav__logo">
      <svg width="79" height="51" viewBox="0 0 79 51" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M21.609 36.3C21.661 37.28 21.661 38.157 21.661 39.137V45.74H37.389V51H0L0 39.138C0 30.061 1.806 23.563 10.778 23.563C16.709 23.563 19.545 26.399 20.778 30.99L37.384 22.326V28.206L21.609 36.3ZM4.435 45.74H17.225V38.726C17.225 33.208 16.657 28.979 10.882 28.979C5.107 28.979 4.435 33.208 4.435 38.726L4.435 45.74Z" fill="#101820"/>
        <path d="M63.822 3.8147e-06C70.579 3.8147e-06 76.508 3.042 78.004 10.211H72.898C71.66 5.931 67.329 4.43501 63.615 4.43501C60.728 4.43501 55.672 5.72501 55.672 9.902C55.672 13.202 58.251 14.853 61.759 15.626L66.09 16.606C71.814 17.843 78.672 20.009 78.672 27.538C78.672 34.81 71.866 38.729 64.441 38.729C55.623 38.729 50.052 33.881 49.072 26.456H54.229C55.209 31.612 58.772 34.294 64.543 34.294C70.112 34.294 73.26 31.715 73.26 28.002C73.26 24.031 69.855 22.484 65.213 21.402L60.572 20.422C55.417 19.287 50.31 16.399 50.31 10.211C50.31 3.042 57.788 3.8147e-06 63.822 3.8147e-06Z" fill="#101820"/>
        <path d="M44.398 51V45.069H50.328V51H44.398Z" fill="#101820"/>
      </svg>
    </router-link>

    <div class="HomeMarketingNav__wrapper">
      <ul class="HomeMarketingNav__list">
        <li v-for="link in navLinks" :key="link.id">
          <router-link v-if="link.url" :to="link.url">{{ link.text }}</router-link>
        </li>
      </ul>

      <button class="HomeMarketingNav__button">
        <span>
          <svg width="22" height="13" viewBox="0 0 22 13" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path id="Path 8510"
              d="M21.1007 6.49956L15.3873 0.786133H12.5306L17.2399 5.49546L0.899353 5.48769L0.900767 7.51284L17.2498 7.51355L12.5306 12.213L15.3866 12.2137L21.1007 6.49956Z"
              fill="#E63E3A"/>
          </svg>
        </span>

        Book a call
      </button>
    </div>
  </div>
</template>

<script lang="js">
import { ref } from "vue"

export default {
  name: 'HomeMarketingNav',

  setup () {
    const navLinks = ref([
      {id: 1, text: 'Services', url: '/'},
      {id: 2, text: 'Case Studies', url: '/'},
      {id: 3, text: 'Blog', url: '/'},
      {id: 4, text: '', url: '/'},
      {id: 5, text: 'We\'re hiring', url: '/'},
      {id: 6, text: 'Contacts', url: '/'}
    ])

    return {
      navLinks
    }
  }
}
</script>

<style lang="scss" scoped>
  .HomeMarketingNav {
    justify-content: space-between;
    padding: 18px 20px;
    position: relative;
    z-index: 1;
    background-color: $red;
    display: grid;
    grid-template-columns: 200px 1fr 0;
    align-items: center;

    &__logo {
      position: relative;
    }

    &__wrapper {
      top: 100%;
      right: -200%;
      transition: right .3s ease-in-out;
      width: auto;
      background-color: $red;
      display: grid;
      justify-content: end;
      position: static;
      grid-template-columns: 2fr 1fr;
      align-items: center;
    }

    &__list {
      background-color: inherit;
      display: grid;
      grid-template-columns: 1fr 1fr 1fr 2fr 1fr 1fr;
      justify-content: center;
      text-align: center;
      padding: 0;

      li {
        list-style: none;
      }

      a {
        color: $color-primary;
        text-decoration: none;
        position: relative;
        transition: color .3s ease-in-out;

        @media screen and (max-width: 1440px) {
          font-size: 18px;
        }

        &:hover {
          color: $white;

          &:after {
            min-width: 100%;
          }
        }

        &:after {
          content: '';
          position: absolute;
          bottom: -2px;
          height: 2px;
          left: 0;
          min-width: 0;
          background-color: $white;
          transition: left .3s ease-in-out, min-width .3s ease-in-out;
        }
      }
    }

    &__button {
      color: $red;
      padding: 10px 18px 10px 150px ;
      display: flex;
      justify-content: center;
      font-size: 22px;
      border: none;
      outline: none;
      position: relative;
      font-weight: 400;
      transition: color .3s ease-in-out, background-color .3s ease-in-out;
      min-width: 200px;
      background-color: $color-primary;
  
      &:hover {
        color: $color-primary;
        background-color: $white;
  
        svg {
          left: calc(50% - 20px);
  
          path {
            fill: $color-primary
          }
        }
      }
  
      svg {
        position: absolute;
        top: calc(50% - 6px);
        left: calc(50% - 60px);
        transition: left .3s ease-in-out;
  
        path {
          transition: fill .3s ease-in-out;
        }
      }
    }
  }
</style>
