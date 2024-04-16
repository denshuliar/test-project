<template>
  <span class="animated-text" ref="textEl" />
</template>

<script lang="js">
import { gsap } from "gsap"
import TextPlugin from "gsap/TextPlugin"
import ScrollTrigger from "gsap/ScrollTrigger"

import {
  ref,
  onMounted
} from "vue"

export default {
  name: 'AppAnimatedText',

  props: {
    text: {
      type: String,
      default: '',
    },
    duration: {
      type: Number,
      default: null
    },
    relatedSection: {
      type: String,
      default: ''
    }
  },

  setup (props) {
    const textEl = ref(null)
    
    onMounted(() => {
      gsap.registerPlugin(ScrollTrigger, TextPlugin)

      gsap.to(textEl.value, {
        scrollTrigger: {
          trigger: textEl.value,
          once: true,
          toggleActions: 'play none none reverse',
        },
        duration: props.duration || 2,
        text: props.text,
        ease: 'none',
        onComplete: () => {
          gsap.to(window, { duration: 1, scrollTo: `#${props.relatedSection}-section` })
        }
      })
    })

    return {
      textEl
    }
  }
}
</script>

