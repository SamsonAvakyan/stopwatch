<template>
  <div class="stopwatch">
    <div class="wrapper">
      <ul class="screens">
        <Screen
          v-for="screen of screens"
          v-bind:key="screen.id"
          v-bind:id="screen.id"
          v-bind:seconds="screen.seconds % 60"
          v-bind:minutes="
            Math.floor(screen.seconds / 60) -
            Math.floor(screen.seconds / 60 / 60) * 60
          "
          v-bind:hours="Math.floor(screen.seconds / 60 / 60)"
          v-bind:isReset="screen.isReset"
          v-bind:isPlay="screen.isPlay"
          @play-stopwatch="toPlay"
          @reset-stopwatch="toReset"
        />
        <AddScreen @add-screen="addStopwatch" />
      </ul>
    </div>
  </div>
</template>

<script>
import Screen from "@/components/Screen.vue";
import AddScreen from "@/components/AddScreen.vue";
export default {
  name: "Stopwatch",
  data() {
    return {
      screens: [],
    };
  },
  components: {
    AddScreen,
    Screen,
  },

  methods: {
    addStopwatch(stopwatch) {
      this.screens.push(stopwatch);
    },
    toPlay(id) {
      for (const s of this.screens) {
        if (s.id === id && s.isPlay) {
          clearInterval(s.interval);
          s.isPlay = !s.isPlay;
        } else if (s.id === id && !s.isPlay) {
          s.interval = setInterval(() => {
            s.seconds += 1;
          }, 1000);
          s.isPlay = !s.isPlay;
        }
      }
    },
    toReset(id) {
      this.screens.map((s) => (s.id === id ? (s.seconds = 0) : s));
    },
  },
};
</script>

<style >
.stopwatch {
  width: 775px;
  margin: auto;
  padding: 72px 0;
  font-size: 22px;
  line-height: 21px;
  color: #9e9e9e;
}

.screens {
  display: grid;
  grid-gap: 45px 50px;
  grid-template-columns: repeat(3, 1fr);
}

@media (max-width: 800px) {
  .stopwatch {
    width: 500px;
  }

  .screens {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 550px) {
  .stopwatch {
    width: 225px;
  }

  .screens {
    grid-template-columns: repeat(1, 1fr);
  }
}
</style>
