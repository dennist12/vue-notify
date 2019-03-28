
<script>
import notification from "./notification";
export default {
  name: "Nofity",
  components: { notification },
  data() {
    return {
      count: 0,
      notifications: []
    };
  },
  methods: {
    add() {
      this.notifications.push({
        id: this.count++,
        title: "New Order",
        type: "info"
        // body: "Dennis",
        // type: "dark. light, danger, warning, info, success"
      });
    },
    remove(notification) {
      this.notifications.splice(this.notifications.indexOf(notification), 1);
    }
  }
};
</script>
<template>
  <div>
    <button @click="add">Add</button>
    <div class="notify">
      <transition-group
        name="custom-classes-transition"
        enter-active-class="animated zoomIn "
        leave-active-class="animated zoomOut "
      >
        <notification
          v-for="(notification) in notifications"
          :key="notification.id"
          :notification="notification"
          @remove="remove(notification)"
        ></notification>
      </transition-group>
    </div>
  </div>
</template>

<style scoped>
.notify {
  position: fixed;
  right: 1rem;
  top: 1rem;
  z-index: 1;
}
</style>
