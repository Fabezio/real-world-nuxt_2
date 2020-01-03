<template lang="pug">
#create
  h1 Event #
    | {{id}}
</template>

<script>
export default {
  head() {
    return {
      title: `Event #${this.id}`,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: `All you wanna know about event #${this.id}`
        }
      ]
    }
  },
  computed: {
    id() {
      return this.$route.params.id
    }
  }
}
</script>

<style scoped></style>
