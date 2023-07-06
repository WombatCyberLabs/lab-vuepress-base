<template>
  <a ref="link" target="_blank">
  </a>
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
    },
    linkText: {
      type: String
    }
  },
 mounted() {
    this.$nextTick(() => {
      const link = this.$refs.link;
      const hostname = window.location.hostname;
      link.href = `${this.protocol}${hostname}:${this.port}${this.path}`;
      if(this.linkText)
        link.innerText = this.linkText;
      else
        link.innerText = link.href;
    });
  }
};
</script>