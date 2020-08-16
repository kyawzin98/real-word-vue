<template>
  <div>
    <h2>Event List</h2>
    <event-card v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import EventCard from "../components/EventCard";
import EventServices from "../services/EventServices";
export default {
  name: "EventList",
  components: { EventCard },
  props: ["id"],
  data: () => ({
    events: []
  }),
  created() {
    EventServices.getEvents()
      .then(response => {
        this.events = response.data;
      })
      .catch(e => {
        console.log("There was a error" + e.response);
      });
  }
};
</script>

<style scoped></style>
