<template>
  <div>
    <h1>
      <strong>👋 Software Engineer</strong>
    </h1>
    <br />
    <p>I build things with JavaScript.</p>
    <p>My preferred toolkit is Vue and Nuxt with TypeScript.</p>
    <p>
      I began at <a href="https://tomandco.co.uk">Tom&Co&nearr;</a> in 2014. I
      joined <a href="https://cazana.com">Cazana&nearr;</a> after they raised
      £750K. 5 years later we were acquired by
      <a href="https://cazoo.co.uk">Cazoo&nearr;</a> for £25M, which is where I
      find myself now.
    </p>
    <br />
    <p>
      <strong>Notes</strong>
    </p>
    <div v-for="link of posts" :key="link.slug">
      <p class="is-size-5">
        <nuxt-link :to="link.path">{{ link.title }}&rarr;</nuxt-link>
      </p>
    </div>
    <br />
    <p><strong>Projects</strong></p>
    <p>
      <a href="https://loequi.uk"><s>LOEQUI&nearr;</s></a>
    </p>
    <small>
      Short lived digital agency side hustle. Lesson learnt: building websites
      for other people is frustrating and not enjoyable.
    </small>
    <p><a href="https://mixbase.co">Mixbase&nearr;</a></p>
    <small>
      On ice. Experiment with scraping and trying to combine data sources to
      make a useful product. Not convinced (yet).
    </small>
    <p><a href="https://matchthread.com">Matchthread&nearr;</a></p>
    <p>
      <small>
        Domain sniped by chance. I've always thought this would make a good site
        name. Realtime match threads to chat with "social betting",
        leaderboards, etc. <strong>Still in ideation.</strong>
      </small>
    </p>
    <br />
    <p><strong>Links</strong></p>
    <p><a href="https://github.com/o8e">GitHub&nearr;</a></p>
    <p><a href="https://linkedin.com/in/otribe/">Linkedin&nearr;</a></p>
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
