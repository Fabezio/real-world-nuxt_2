<template lang="pug">
#create
  h1 {{event.title}}
</template>

<script>
import { mapState } from 'vuex'
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
  computed: mapState({
    events: (state) => state.events.event
  }),
  async fetch({ store, error, params }) {
    try {
      await store.dispatch('events/fetchEvent', params.id)
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
