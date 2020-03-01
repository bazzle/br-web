<template>
  <div>
    <BlogFeed :postFeed="posts" />
    <AboutBlog :aboutData="about" />
  </div>
</template>

<script>
  import {createClient} from '~/plugins/contentful.js'
  import AboutBlog from '~/components/AboutBlog'
  import HomeHero from '~/components/HomeHero'
  import BlogFeed from '~/components/BlogFeed'

  const client = createClient()

  export default {
    asyncData ({env}) {
      return Promise.all([
        client.getEntries({
          'content_type': env.CTF_BLOG_POST_TYPE_ID,
          order: '-sys.createdAt'
        }),
        client.getEntries({
          'content_type': env.CTF_ABOUT_TYPE_ID
        }),
        client.getEntries({
          'content_type': env.CTF_HERO_TYPE_ID
        }),
      ]).then(([posts, about, hero]) => {
        return {
          posts:posts.items,
          about:about.items[0],
          hero:hero.items[0]
        }
      }).catch(console.error)
    },
    data(){
      return{
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
            href: "https://www.linkedin.com/in/br-web/",
            linkText: "LinkedIn",
            target: "_blank"
          }
        ]
      }
    },
    components: {
      HomeHero,
      AboutBlog,
      BlogFeed
    }
  }
</script>
