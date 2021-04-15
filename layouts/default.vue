<template>
  <main>
    <Nuxt />
  </main>
</template>

<style lang="sass">
*
  box-sizing: border-box
html,
body
  margin: 0
body
  font-family: 'Inconsolata', monospace
  background: black
  color: gray
  line-height: 1.5
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
  color: white
s
  color: gray
</style>

<style lang="sass">
[hidden]
  display: none
a
  color: #FF4365
  &:link,
  &:visited
    color: #FF4365
  &:focus,
  &:hover
    color: darken(#FF4365, 15%)
  &:active
    color: darken(#FF4365, 30%)
.abbr
  border-bottom: 1px dotted currentColor
  cursor: crosshair
</style>
