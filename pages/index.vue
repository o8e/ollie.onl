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
    <!-- <p>
      My professional career started in 2014, working for an e-commerce agency
      using Angular. I learned a lot from some clever sausages, but agency life
      sucks and so does&nbsp;Magento.
    </p>
    <p>
      I joined <a href="https://cazana.com">Cazana</a> in 2016 as one of the
      first hires as a startup. Fast forward having built a bunch of powerful
      products for the Automotive industry.
    </p> -->
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
    <p><strong>What's new</strong></p>
    <span><strong>&mdash;</strong></span>
    <div v-for="(commit, index) in commits" :key="index" class="commits">
      <div>[{{ commit.author.login }}] {{ commit.commit.message }}</div>
      <div>
        <a :href="commit.html_url">{{ commit.sha.slice(0, 7) }}</a>
        {{ timeAgo(commit.commit.author.date) }}
      </div>
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
  async asyncData({ $axios, $content }) {
    const posts = await $content('notes').fetch()
    const { data: commits } = await $axios.get(
      'https://api.github.com/repos/o8e/ollie.onl/commits?per_page=3'
    )

    return {
      posts,
      commits,
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
