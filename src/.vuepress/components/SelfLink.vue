<template>
  <a :href="getLinkUrl()" target="_blank">
    {{ getLinkUrl() }}
  </a>
</template>

<script>
export default {
  props: {
    port: {
      type: Number,
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
  methods: {
    getLinkUrl() {
      const hostname = window.location.hostname;
      return `${this.protocol}${hostname}:${this.port}${this.path}`;
    }
  }
};
</script>