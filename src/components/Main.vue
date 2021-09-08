<template>
  <div class="wrapper">
    <div class="options">
      <stroke
        class="kit"
        :selected="selected['stroke']"
        @click.native="setSelect('stroke')"
      ></stroke>
      <eraser-control
        class="kit"
        :selected="selected['eraser']"
        @click.native="setSelect('eraser')"
      ></eraser-control>
      <thickness class="kit" @thick-change="changeThick"></thickness>
      <text-control
        class="kit"
        :selected="selected['text-control']"
        @click.native="setSelect('text-control')"
      ></text-control>
      <clean class="kit" @click.native="cleanCanvas"></clean>
      <color-board class="kit" @color-selected="changeColor"></color-board>
    </div>
    <div class="anchor">
      <textarea ref="textBox" class="text-box"></textarea>
    </div>
    <canvas :width="width" :height="height" id="vue-drawing-main-canvas">
      We are very sorry that this browser doesn't support canvas.
    </canvas>
    <export-control
      class="export"
      @click.native="exportCanvas"
    ></export-control>
  </div>
</template>

<script>
  import VueDrawing from "./js/VueDrawing";
  import Stroke from "./kits/stroke";
  import EraserControl from "./kits/eraser";
  import ColorBoard from "./kits/color-board";
  import Thickness from "./kits/thickness";
  import Clean from "./kits/clean";
  import ExportControl from "./kits/export-control";
  import TextControl from "./kits/text-control";
  import TextInput from "./js/TextInput";
  import Eraser from "./js/Eraser";

  export default {
    name: "vue-drawing",
    components: {
      TextControl,
      Clean,
      Thickness,
      ColorBoard,
      EraserControl,
      Stroke,
      ExportControl
    },
    props: {
      width: {
        type: Number,
        default: 500
      },
      height: {
        type: Number,
        default: 300
      }
    },
    data() {
      return {
        drawing: null,
        selected: {
          stroke: true,
          eraser: false,
          "text-control": false
        },
        textControlStyle: null,
        textValue: null,
        showText: false
      };
    },
    methods: {
      setSelect(name) {
        for (let i in this.selected) {
          this.selected[i] = i === name;
        }
        this[name]();
      },
      stroke() {
        this.drawing.restoreTool();
      },
      eraser() {
        let eraser = new Eraser();
        this.drawing.use(eraser);
      },
      "text-control"() {
        let textInput = new TextInput(this.$refs.textBox);
        this.drawing.use(textInput);
      },
      changeColor(color) {
        this.drawing.style.strokeColor = color;
      },
      changeThick(thick) {
        this.drawing.style.strokeWidth = thick;
      },
      cleanCanvas() {
        this.drawing.clean();
      },
      exportCanvas() {
        this.$emit(
          "image-export",
          this.drawing.project.exportSVG({ asString: true })
        );
      }
    },
    mounted() {
      this.drawing = new VueDrawing("vue-drawing-main-canvas");
    }
  };
</script>

<style scoped lang="scss">
.wrapper {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  flex-direction: column;
}

.options {
  width: 900px;
  overflow: hidden;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  margin-bottom: 10px;
}

#vue-drawing-main-canvas {
  border: solid #ddd 1px;
  border-radius: 5px;
  cursor: crosshair;
  position: relative;
}

.text-box {
  display: none;
  position: absolute;
  width: 0;
  height: 0;
  z-index: 100;
  border: dashed blueviolet 1px;
}
.kit {
  margin-right: 10px;
}
.anchor {
  position: relative;
  width: 0;
  height: 0;
}
</style>
