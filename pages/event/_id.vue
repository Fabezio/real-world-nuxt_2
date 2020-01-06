<template lang="pug">
div
  .event-header
    span.eyebrow @{{ event.time }} on {{ parsedDate}}
    h1.title {{ event.title }}
    h5 Organized by {{ event.organizer ? event.organizer.name : '' }}
    h5 Category: {{ event.category }}
  BaseIcon(name='map')
    h2 Location
  address {{ event.location }}
  h2 Event details
  p {{ event.description }}
  h2
    | Attendees
    span.badge.-fill-gradient {{ event.attendees.length }}
  ul.list-group
    li.list-item(v-for='(attendee, index) in event.attendees', :key='index')
      b {{ attendee.name }}
//#create
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
    event: (state) => state.events.event,
    parsedDate() {
      const eventDate = new Date(this.event.date)
      return eventDate.toDateString()
    }
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
