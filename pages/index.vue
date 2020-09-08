<template>
    <div class="container">
        <span v-model="message"></span>
        <canvas id="canvas" width="600" height="600">
            Canvas requires a browser that supports HTML5.
        </canvas>
    </div>
</template>

<script>
export default {
    data: {
        vueCanvas: null,
        message: "text"
    },
    mounted: function() {
        const canvas = document.getElementById("canvas");
        const ctx = canvas.getContext("2d");
        this.vueCanvas = ctx;
    },
    methods: {
        drawImage() {
            this.vueCanvas.clearRect(0, 0, 600, 600);
            this.vueCanvas.fillStyle = "Black";
            this.vueCanvas.font = "48px serif";
            this.vueCanvas.fillText("Hello world", 10, 50);
        }
    },
};
</script>

<style lang="scss">
.red {
    color: red;
}
</style>
