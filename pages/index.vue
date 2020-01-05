<template lang="pug">
  div
    h1 Events
    EventCard(v-for='(event, index) in events', :key='index', :event='event', :data-index='index')

</template>

<script>
import { mapState } from 'vuex'
import EventCard from '@/components/EventCard.vue'
export default {
  components: {
    EventCard
  },
  head() {
    return {
      title: 'Events Listing '
    }
  },
  computed: mapState({
    events: (state) => state.events.events
  }),
  async fetch({ store, error }) {
    try {
      await store.dispatch('events/fetchEvents')
    } catch (e) {
      error({
        statusCode: 503,
        message: 'Unable to fetch events at this time. Please try again.'
      })
    }
  }
}
</script>

<style scoped></style>
