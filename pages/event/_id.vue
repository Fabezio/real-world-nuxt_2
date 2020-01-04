<template lang="pug">
#create
  h1 {{event.title}}
</template>

<script>
export default {
  head() {
    return {
      title: this.event.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: `All you wanna know about event #${this.event.title}`
        }
      ]
    }
  },
  async asyncData({ $axios, error, params }) {
    try {
      const { data } = await $axios.get(
        `http://localhost:3000/events/${params.id}`
      )
      return { event: data }
    } catch (e) {
      error({
        statusCode: 503,
        message: `Unable to fetch event #${params.id} at this time. Please select another one.`
      })
    }
  }
}
</script>

<style scoped></style>
