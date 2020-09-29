<template>
  <div class="screen">
    <div class="screen__top" v-bind:class="{ active: isPlay }">
      <div class="time">
        {{
          (hours ? hours + ":" : "") + (minutes ? minutes + ":" : "") + seconds
        }}
      </div>
    </div>
    <div class="screen__bottom">
      <div class="play-pause">
        <div
          v-bind:class="{ play: !isPlay, pause: isPlay, backlight: isPlay }"
          @click="$emit('play-stopwatch', id)"
        />
      </div>
      <div
        class="reset"
        @click="$emit('reset-stopwatch', id)"
        v-bind:class="{ backlight: isPlay }"
      />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    seconds: {
      type: Number,
    },
    minutes: {
      type: Number,
    },
    hours: {
      type: Number,
    },
    id: {
      type: Number,
    },
    isPlay: {
      type: Boolean,
    },
  },
};
</script>

<style >
.screen {
  background-color: #696969;
  width: 225px;
}

.screen__top {
  border-bottom: 1px solid #9e9e9e;
  padding: 19px 75px;
}

.time {
  text-align: center;
}

.screen__bottom {
  display: flex;
  justify-content: space-between;
  padding: 20px 70px;
}

.play {
  width: 0;
  height: 0;
  border-top: 10px solid transparent;
  border-left: 17px solid #9e9e9e;
  border-bottom: 10px solid transparent;
  cursor: pointer;
}

.pause {
  width: 10px;
  height: 20px;
  background-color: #9e9e9e;
  position: relative;
  cursor: pointer;
}

.pause::after {
  content: "";
  position: absolute;
  top: 0;
  left: 3px;
  width: 4px;
  height: 100%;
  background-color: #696969;
}

.reset {
  width: 20px;
  height: 20px;
  background-color: #9e9e9e;
  cursor: pointer;
}

.hidden {
  display: none;
}

.active {
  color: #fff;
  border-bottom: 1px solid #fff;
}

.backlight {
  background-color: #fff;
}
</style>