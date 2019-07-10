<template>
  <div id="app">
    <input type="button" value="create frames" @click="createFrames">
  <input type="button" value="delete frames" @click="deleteFrames">  
  </div>
</template>

<script>

export default {
  name: 'app',
  data: () => ({
    frames: [],
    videoFile: null,
    frame: null,
  }),
  created() {
    window.vue = this
  },
  methods: {
    createFrames() {
      let frame = new cv.Mat.ones(720, 1280, cv.CV_8UC4)
      for (let i = 0; i < 80; i++) {
        this.frames.push(frame.clone())
      }
    },
    deleteFrames() {
      for (let frame of this.frames) {
        frame.delete()
      }
      this.frames = []
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
