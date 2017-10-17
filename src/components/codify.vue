<template>
    <h1 v-on:click="run">{{ msg }}</h1>
</template>

<script>
export default {
  name: 'Codify',
  props: ['hi'],
  data() {
    return {
      msg: 'what what what',
      original: '',
      chars: 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789#%$&',
      running: false,
      interval: null,
      decodespeed: 2,
      count: 0,
      runspeed: 30,
      decodeCount: 0,
    };
  },

  created: function init() {
    this.original = this.msg;
  },

  methods: {
    encode: function encodify() {
      const modifier = (this.msg.length - this.decodeCount);
      const toChange = Math.floor(Math.random() * modifier) + this.decodeCount;
      const randomChar = this.chars.charAt(Math.floor(Math.random() * this.chars.length));
      this.msg = this.msg.substr(0, toChange) + randomChar + this.msg.substr(toChange + 1);
    },
    decode: function decodify() {
      const toChange = this.decodeCount;
      const originalChar = this.original.charAt(toChange);
      this.msg = this.msg.substr(0, toChange) + originalChar + this.msg.substr(toChange + 1);
      this.decodeCount += 1;
    },
    codify: function codifiy() {
      this.running = true;
      if (this.count >= this.decodespeed) {
        this.decode();
        if (this.msg === this.original) {
          clearInterval(this.interval);
          this.count = 0;
          this.running = false;
          this.decodeCount = 0;
          return;
        }
        this.count = 0;
        return;
      }
      this.encode();
      this.count += this.runspeed / 100;
    },
    run: function codify() {
      if (this.running) {
        return;
      }
      this.interval = setInterval(this.codify, this.runspeed);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
