<template>
  <main>
    <Nuxt />
  </main>
</template>

<style lang="sass">
$background: #11151C
$text: #C5CBD3
$link: #D66853
*
  box-sizing: border-box
html,
body
  margin: 0
body
  font-family: monospace
  background: $background
  color: $text
  line-height: 1.75
  font-size: 16px
main
  padding: 3rem 1.5rem
  max-width: 40rem
  margin-left: auto
  margin-right: auto
h1,
h2,
h3,
h4,
h5,
h6,
strong
  color: $text
a
  color: $link
  &:link,
  &:visited
    color: $link
  &:focus,
  &:hover
    color: darken($link, 15%)
  &:active
    color: darken($link, 30%)
.abbr
  border-bottom: 1px dotted currentColor
  cursor: crosshair
</style>
