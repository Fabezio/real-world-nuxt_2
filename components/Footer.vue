<template lang="pug">
  footer
    .container
      p
      | &copy; 2019 |
      i.fa.fa-value(aria-hidden='true') &nbsp;
      a(href='https://github.com/Fabezio/real-world-nuxt_2.git' title='my code version')
        button.button View Source
</template>

<script>
export default {}
</script>

<style scoped>
footer {
  position: absolute;
  bottom: 0;
  width: 100%;
  display: block;
}
a {
  cursor: pointer;
}
a .button {
  border: 1px solid darkslategray;
  border-radius: 5px;
  padding: 8px;
}
a .button:hover {
  background: whitesmoke;
  color: none;
}
</style>
