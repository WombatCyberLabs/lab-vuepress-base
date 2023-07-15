<template>
	<div>
	  <a @click="downloadConfig()">Download Config</a>
	  <iframe ref="iframe" style="display:none"></iframe>
	</div>
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
  methods:{
    downloadConfig() {
      this.$nextTick(() => {
        const iframe = this.$refs.iframe;
        const hostname = window.location.hostname;
        iframe.src = `${this.protocol}${hostname}:${this.port}${this.path}`;
      });
    }
  }
};
</script>
