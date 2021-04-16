<template>
  <div>
    <h1>
      <strong>
        Frontend Engineer with an
        <span v-tippy="{ html: '#tooltip', followCursor: true }" class="abbr">
          evergrowing list of side&nbsp;projects.
        </span>
      </strong>
    </h1>
    <br />
    <p><strong>About</strong></p>
    <span><strong>&mdash;</strong></span>
    <p>I build things with JavaScript, using Vue and&nbsp;Nuxt.</p>
    <p>
      Currently working at <a href="https://cazana.com">Cazana</a> developing
      products for the automotive industry.
    </p>
    <br />
    <p>
      <strong>Notes</strong>
    </p>
    <span><strong>&mdash;</strong></span>
    <div v-for="link of posts" :key="link.slug">
      <p class="is-size-5">
        <nuxt-link :to="link.path">
          {{ link.title }}
        </nuxt-link>
      </p>
    </div>
    <div id="tooltip" hidden>
      <video autoplay loop muted playsinline width="250">
        <source src="/spoderman.webm" type="video/webm" />
        <source src="/spoderman.mp4" type="video/mp4" />
        Sorry, your browser doesn't support embedded videos.
      </video>
    </div>
    <br />
    <p><strong>Links</strong></p>
    <p><strong>&mdash;</strong></p>
    <p><a href="https://github.com/o8e">GitHub</a></p>
    <p><a href="https://twitter.com/shiinotik">Twitter</a></p>
  </div>
</template>

<script>
import { formatDistance } from 'date-fns'
export default {
  async asyncData({ $content }) {
    const posts = await $content('notes').fetch()
    return {
      posts,
    }
  },
  head() {
    return {
      title: 'o8e (ollie)',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content:
            'Frontend Engineer with an evergrowing list of side projects',
        },
        { hid: 'og:title', property: 'og:title', content: 'o8e (ollie)' },
        {
          hid: 'og:description',
          property: 'og:description',
          content:
            'Frontend Engineer with an evergrowing list of side projects',
        },
        {
          hid: 'twitter:title',
          name: 'twitter:title',
          content: 'o8e (ollie)',
        },
        {
          hid: 'twitter:description',
          name: 'twitter:description',
          content:
            'Frontend Engineer with an evergrowing list of side projects',
        },
      ],
    }
  },
  methods: {
    timeAgo(date) {
      return formatDistance(new Date(date), new Date(), { addSuffix: true })
    },
  },
}
</script>

<style lang="sass" scoped>
h1
  font-size: 18px
img
  width: 250px
.commits
  display: flex
  flex-flow: row wrap
  justify-content: space-between
  div
    &:last-of-type
      text-align: right
</style>
