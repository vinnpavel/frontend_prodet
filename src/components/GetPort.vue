<script>
export default {
  props: {
    host: String,
    url: String
  },

  emits: ['response'],

  data() {
    return {
      portId: null
    }
  },

  methods: {
    async fetchPort() {
      this.portId = null;
      const res = await fetch(this.url, {method: 'POST'});
      this.portId = await res.json();
      if (this.portId) {
        this.$emit('response', this.portId)
      }
    }
  }
}
</script>

<template>
  <div>
    <button @click="fetchPort">Fetch port</button>
    <pre v-if="!portId">Press the button to get free port</pre>
    <pre v-else>Now enter "{{ host }}" in the Host field
and "{{ portId.port }}" in the Port field to find
out your device's protocol
    </pre>
  </div>
</template>

<style>

</style>
