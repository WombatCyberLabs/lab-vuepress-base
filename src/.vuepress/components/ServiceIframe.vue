<template>
  <iframe ref="iframe" style="width:100%;height:600px"></iframe>
</template>

<script>
export default {
  props: {
    port: {
      type: String,
      required: true
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