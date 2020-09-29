<template>
  <div class="add-btn" @click="onAddScreen" />
</template>

<script>
export default {
  methods: {
    onAddScreen() {
      const newStopwatch = {
        id: Date.now(),
        seconds: 0,
        minutes: 0,
        hours: 0,
        isPlay: false,
        isReset: false,
        interval: null,
      };
      this.$emit("add-screen", newStopwatch);
    },
  },
};
</script>

<style scoped>
.add-btn {
  background-color: #696969;
  position: relative;
  min-height: 120px;
  cursor: pointer;
}

.add-btn::before {
  content: "";
  position: absolute;
  top: calc(50% - 10px);
  left: calc(50%);
  width: 3px;
  height: 20px;
  background-color: #9e9e9e;
  cursor: pointer;
}

.add-btn::after {
  content: "";
  position: absolute;
  top: calc(50% - 1.5px);
  left: calc(50% - 8.5px);
  width: 20px;
  height: 3px;
  background-color: #9e9e9e;
  cursor: pointer;
}
</style>