<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        explore-nuxt
      </h1>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          rel="noopener noreferrer"
          class="button--green"
        >
          Documentation
        </a>
        <nuxt-link
          v-for="post in posts"
          :to="{ name: 'posts-id', params: { id: post.id } }"
          :key="post.id"
          class="button--grey"
        >
          {{ post.title }}
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    head () {
      return {
        title: 'Home Page 🍕',
        meta: [
          { name: 'twitter:title', content: 'Nuxt Fundamentals'},
          { name: 'twitter:description', content: 'Exploring Nuxt by example = 🍕'},
          { name: 'twitter:image', content: 'https://i.imgur.com/UYP2umJ.png'},
          { name: 'twitter:card', content: 'summary_large_image'}
        ]
      }
    },

    async asyncData({ params, $axios}) {
      let response = await $axios.get('posts')
      console.log('axios module !!')
      return {
        posts: response.data
      }
    },
  }
</script>

<style scoped>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
}

.links {
  padding-top: 15px;
}
</style>
