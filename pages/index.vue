<template>
  <div class="container">
    <section class="hero">
      <div class="hero-body">
        <h1 class="title">meme template</h1>
      </div>
    </section>

    <div class="columns">
      <div class="column">
        <div class="field">
          <label class="label">Message</label>
          <div class="control">
            <textarea
              v-on:keyup="drawImage"
              v-model="message"
              class="textarea"
              placeholder="Textarea"
            ></textarea>
          </div>
        </div>
        <div class="field is-grouped">
          <div class="control">
            <a @click="saveImage" class="button is-link">Save</a>
          </div>
          <div class="control">
            <button class="button is-link is-light">Clear</button>
          </div>
        </div>
      </div>
      <div class="column">
        <canvas id="canvas" width="600" height="600">Canvas requires a browser that supports HTML5.</canvas>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      vueCanvas: null,
      message: "text",
    };
  },
  mounted: function () {
    const canvas = document.getElementById("canvas");
    const ctx = canvas.getContext("2d");
    this.vueCanvas = ctx;
    this.drawImage();
  },
  methods: {
    drawImage() {
      this.vueCanvas.clearRect(0, 0, 600, 600);
      this.vueCanvas.fillStyle = "black";
      this.vueCanvas.font = "48px serif";
      this.vueCanvas.fillText(this.message, 10, 50);
    },
    saveImage(e) {
        console.log(this.vueCanvas);
        e.target.href = document.getElementById("canvas").toDataURL();
        e.target.download = "meme.png";
    }
  },
};
</script>

<style lang="scss">
.red {
  color: red;
}
</style>
