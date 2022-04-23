<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <h1>{{ convertTime(watch) }}</h1>
    <h1>HH:MM:SS</h1>
    <button @click="start" class="mr-10">start</button>
    <button @click="stop" class="mr-10">stop</button>
    <button @click="reset">reset</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      watch: 0,
      timer: null,
    };
  },
  methods: {
    start: function () {
      if (!this.timer) this.timer = setInterval(() => (this.watch += 1), 1000);
    },
    reset: function () {
      this.watch = 0;
      if (this.timer) {
        clearInterval(this.timer);
        this.timer = null;
      }
    },
    stop: function () {
      if (this.timer) {
        clearInterval(this.timer);
        this.timer = null;
      }
    },
    convertTime: function (totalSeconds) {
      const hours = Math.floor(totalSeconds / 3600);
      totalSeconds %= 3600;
      const minutes = Math.floor(totalSeconds / 60);
      const seconds = (totalSeconds %= 60);
      return (
        String(hours).padStart(2, "0") +
        ":" +
        String(minutes).padStart(2, "0") +
        ":" +
        String(seconds).padStart(2, "0")
      );
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.mr-10 {
  margin-right: 10px;
}
</style>
