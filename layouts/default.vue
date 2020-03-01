<template>
  <div :class="darkMode === true ? 'dark-mode' : 'light-mode'" id="pageTop">
    <BlogHeader v-on:darkMode = "darkModeUpdate" />
    <main role="main">
      <nuxt/>
    </main>
    <BackTop />
  </div>
</template>
<script>
import BlogHeader from '~/components/BlogHeader.vue'
import BackTop from '~/components/BackTop.vue'
export default {
  data(){
    return{
      darkMode: true,
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
    }
  },
  components: {
    BlogHeader,
    BackTop
  }
}
</script>