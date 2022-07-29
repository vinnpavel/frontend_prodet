<script>
export default {
  props: {
    port: Number,
    time: Number,
    url: String
  },
  data() {
    return {
      portData: null
    }
  },
  methods: {
    async detectProtocol() {
      this.portData = null;
      const urlGet = `${this.url}?port_uid=${this.port}-${this.time}`
      const res = await fetch(urlGet, {method: 'GET'});
      this.portData = await res.json()
    }
  }
}
</script>

<template>
  <pre></pre>
  <div v-if="port">
    <button @click="detectProtocol">Detect protocol</button>
    <pre v-if="!portData">Press the button if you connected the device</pre>
    <pre v-else>Detected protocols: {{ portData.protocols.toString() }}
    </pre>
  </div>
</template>

<style>

</style>
