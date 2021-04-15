<template>
  <article>
    <nuxt-link to="/">&larr; Go back</nuxt-link>
    <h1>{{ post.title }}</h1>
    <nuxt-content :document="post" />
    <br />
    <a
      class="github"
      :href="`https://github.com/o8e/ollie.onl/blob/master/content/notes/${post.slug}.md`"
    >
      Read on GitHub &para;
    </a>
    <br />
    <no-ssr>
      <a class="twitter" :href="`http://twitter.com/share?url=${url}`">
        Share on Twitter &weierp;
      </a>
    </no-ssr>
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const post = await $content('notes', params.slug).fetch()

    return {
      post,
    }
  },
  head() {
    return {
      title: `${this.post.title}`,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.post.description,
        },
        { hid: 'og:title', property: 'og:title', content: this.post.title },
        {
          hid: 'og:description',
          property: 'og:description',
          content: this.post.description,
        },
        {
          hid: 'twitter:title',
          name: 'twitter:title',
          content: this.post.title,
        },
        {
          hid: 'twitter:description',
          name: 'twitter:description',
          content: this.post.description,
        },
      ],
    }
  },
  computed: {
    url() {
      if (process.client) {
        return window?.location?.href
      }

      return null
    },
  },
}
</script>

<style lang="sass">
pre[class*="language-"]
  line-height: 1.25
  font-size: 14px
</style>

<style lang="sass" scoped>
.github
  color: #fafafa
  &:link,
  &:visited
    color: #fafafa
  &:focus,
  &:hover
    color: darken(#fafafa, 15%)
  &:active
    color: darken(#fafafa, 30%)
.twitter
  color: #6CADDE
  &:link,
  &:visited
    color: #6CADDE
  &:focus,
  &:hover
    color: darken(#6CADDE, 15%)
  &:active
    color: darken(#6CADDE, 30%)
</style>
