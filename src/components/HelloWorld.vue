<template>
  <div
    class="box"
    @drop.capture="isActiveDrag($event)"
    @dragover.prevent.stop
    @dragleave="hiddenDrag($event)"
  >
    <div class="divx" @dragover.prevent="showDrag($event)" id="list" v-if="!statusDiv"></div>
    <div class="form" v-if="statusDiv">
      <input type="file" class="filex" multiple>
    </div>
    {{statusDiv}}
  </div>
</template>

<script>
export default {
  data() {
    return {
      valorx: null,
      statusDiv: false
    };
  },
  methods: {
    isActiveDrag(e) {
      if (e.target.className !== "filex") {
        e.preventDefault();
      }
    },
    showDrag(e) {
      this.statusDiv = true;
    },
    hiddenDrag(e) {
      if (e.target.className === "filex") {
        this.statusDiv = false;
      }
    }
  }
};
</script>
<style lang="scss" scoped>
.box {
  background: #eee;
  width: 100%;
  height: 600px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  .mostraDrag {
    .hide {
      display: none;
    }
  }
  .form {
    background-color: #ccc;
    width: 300px;
    height: 300px;
    position: relative;

    .filex {
      background: red;
      position: absolute;
      top: 0;
      bottom: 0;
      left: 0;
      right: 0;
      width: 100%;
    }
  }
  .divx {
    background: #ccc;
    width: 300px;
    height: 300px;
  }
}
</style>

