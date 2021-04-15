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
    <p><strong>&mdash;</strong></p>
    <p>I build things with JavaScript, using Vue and&nbsp;Nuxt.</p>
    <p>
      My professional career started in 2014, working for an e-commerce agency
      using Angular. I learned a lot from some clever sausages, but agency life
      sucks and so does&nbsp;Magento.
    </p>
    <p>
      I joined <a href="https://cazana.com">Cazana</a> in 2016 as one of the
      first hires as a startup. Fast forward having built a bunch of powerful
      products for the Automotive industry.
    </p>
    <br />
    <p>
      <strong>Notes</strong>
    </p>
    <div v-for="link of posts" :key="link.slug">
      <p class="is-size-5">
        <nuxt-link :to="link.path">
          {{ link.title }}
        </nuxt-link>
      </p>
    </div>
    <div id="tooltip" hidden>
      <img
        width="250"
        src="/spoderman.gif"
        alt="A gif of spiderman pointing at himself"
      />
    </div>
  </div>
</template>

<script>
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
}
</script>

<style lang="sass" scoped>
h1
  font-size: 16px
img
  width: 250px
</style>
