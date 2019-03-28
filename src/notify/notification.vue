<script>
export default {
  name: "Notification",
  props: {
    notification: {
      type: Object,
      required: true,
      default: () => {
        return {};
      }
    }
  },
  data() {
    return {
      timeout: null
    };
  },
  methods: {
    remove(d) {
      clearTimeout(this.timeout);
      this.$emit("remove", this.notification);
    }
  },
  mounted() {
    this.timeout = setTimeout(() => {
      this.remove(this.notification);
    }, 3000);
  }
};
</script>
<template>
  <div class="notification callout animated" :class="notification.type">
    <strong>{{ notification.title }}</strong>
    <small>{{ notification.body }}</small>
  </div>
</template>
<style scoped>
.notification {
  margin-top: 0.8rem;
  padding: 0.8rem 0.6rem;
  border-radius: 0.2rem;
  box-shadow: 0 1px 0.4rem 0.1rem rgba(0, 0, 0, 0.1);
}
.notification.success {
  background: rgb(8, 163, 8);
  color: #ffff;
}
.notification.danger {
  background: rgb(209, 19, 19);
  color: #fff;
}
.notification.warning {
  background: rgb(228, 132, 22);
  color: #222;
}
.notification.info {
  background-color: rgb(35, 136, 219);
  color: #fff;
}
.notification.dark {
  background-color: rgb(20, 20, 20);
  color: #fff;
}
.notification.light {
  background-color: #ffff;
  color: #222;
}
.notification strong {
  display: block;
}
</style>
