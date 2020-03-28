<template>
  <a :href="generatedUrl" :class="size" title="Git-repository" aria-label="Facebook">
    <facebook-icon class="icon" />
    {{text}}
  </a>
</template>

<script>
import { FacebookIcon  } from 'vue-feather-icons'

export default {
  data() {
    return {
      currentUrl: '',              
    }
  },
  computed: {
    generatedUrl()
    {
      console.log('https://www.facebook.com/sharer/sharer.php?caption='+this.title+'&u='+this.currentUrl)
      return 'https://www.facebook.com/sharer/sharer.php?caption='+this.title+'&u='+this.currentUrl
    }
  },
  components: {
    FacebookIcon
  },
  props: {
    size: {
      type: String,
      default: 'small'
    },
    title: {
      type: String,
      default: 'D'
    },
    text: {
      type: String,
      default: 'Udostępnij na FB'
    }
  },
  mounted()
  {
    this.currentUrl = document.URL
  }
}
</script>

<style lang="scss" scoped>
a {
  display: inline-block;
  padding: 6px 10px;
  text-decoration: none;
  border-radius: 3px;
  font-size: 12px;
  line-height: 18px;
  font-weight: 700;
  transition: color .15s ease-in-out, background .15s ease-in-out;

  &:focus {
    outline: none;
  }

  .dark & {
    color: $textBright;
    background: $backgroundBright;
  }

  .bright & {
    color: $textDark;
    background: $backgroundDark;
  }

  svg {
    width: 18px;
    height: 18px;
    vertical-align: -6px;
    margin-right: 4px;
  }

  &.large {
    @include respond-above(sm) {
      font-size: 18px;
      padding: 12px 20px;
      line-height: 24px;

      svg {
        width: 24px;
        height: 24px;
      }
    }
  }
}
</style>