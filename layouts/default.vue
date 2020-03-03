<template>
  <div :class="darkMode === true ? 'dark-mode' : 'light-mode'" id="pageTop">
    <BlogHeader v-on:darkMode = "darkModeUpdate" />
    <main role="main">
      <nuxt/>
    </main>
    <no-ssr>
      <BackTop v-if="this.scrolledTop === true" />
    </no-ssr>
  </div>
</template>
<script>
import BlogHeader from '~/components/BlogHeader.vue'
import BackTop from '~/components/BackTop.vue'
export default {
  data(){
    return{
      darkMode: true,
      scrolledTop: false,
      links: [
        {
          id: "email",
          href: "mailto:barry@br-web.io",
          linkText: "email",
          target: "_self"
        },
        {
          id: "cv",
          href: "https://br-web.io/cv.pdf",
          linkText: "CV (PDF)",
          target: "_blank"
        },
        {
          id: "LinkedIn",
          href: "https://br-web.io/cv.pdf",
          linkText: "CV (PDF)",
          target: "_blank"
        }
      ]
    }
  },
  methods: {
    darkModeUpdate: function(){
      this.darkMode === true ? this.darkMode = false : this.darkMode = true
    },
    checkTop(){
      const contentstart = document.querySelector('body');
      const contentoffset = contentstart.getBoundingClientRect().top + pageYOffset;
      if ( pageYOffset === 0 ){
        this.scrolledTop = false
      } else {
        this.scrolledTop = true
      }
    }
  },
  mounted() {
    document.addEventListener('scroll', this.checkTop);
  },
  destroyed() {
    document.removeEventListener('scroll', this.checkTop);
  },
  components: {
    BlogHeader,
    BackTop
  }
}
</script>