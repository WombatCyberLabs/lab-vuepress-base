<template>
  <iframe ref="iframe" style="display:none"></iframe>
</template>

<script>
export default {
  props: {
    port: {
      type: String,
      default: "8081"
    },
    protocol: {
      type: String,
      default: 'http://' // Default protocol value
    },
    path: {
      type: String,
      default: '/'
    }
  },
 mounted() {
    this.$nextTick(() => {
      const iframe = this.$refs.iframe;
      const hostname = window.location.hostname;
      iframe.src = `${this.protocol}${hostname}:${this.port}${this.path}`;
    });
  }
};
</script>