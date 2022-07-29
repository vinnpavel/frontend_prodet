<script>
import GetPort from './components/GetPort.vue'
import GetProtocol from './components/GetProtocol.vue'

export default {
  components: {
    GetPort,
    GetProtocol
},
  data() {
    return {
      prodet: {
        host: '0.0.0.0',
        portProdet: '8897',
        get url() {
          return `http://${this.host}:${this.portProdet}/v0/port`
        }
      },
      portReady: null
    }
  }
}
</script>

<template>
  <main>
    <pre>This service can help you to detect protocol of your device</pre>
    <pre></pre>
    <GetPort v-bind="prodet" @response="(msg) => portReady = msg"/>
    <GetProtocol v-bind="portReady" :url="prodet.url"/>
  </main>
</template>

<style>

</style>
