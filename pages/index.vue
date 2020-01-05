<template lang="pug">
  div
    h1 Events
    EventCard(v-for='(event, index) in events', :key='index', :event='event', :data-index='index')

</template>

<script>
import EventCard from '@/components/EventCard.vue'
import {mapState} from 'vuex'
export default {
  components: {
    EventCard
  },
  head() {
    return {
      title: 'Events Listing '
    }
  },
  async asyncData({ error }) {
    try {
      const { data } = await EventService.getEvents()
      return { events: data }
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
