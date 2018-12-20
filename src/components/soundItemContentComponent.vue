<template>
<div>
  <button @click.prevent="playPauseSound(); updateProgress()">
    <audio ref="audioFile" :src="soundItem.url"></audio>
    <img class="audio-item-image" :src="soundItem.image" />
    <div class="audio-item-title">
      {{ soundItem.title }}
      <div class="audio-item-progress" :style="{'width': widthProgress}"></div>
    </div>
  </button>
</div>
</template>
<script>
export default {
  props: ['soundItem'],

  data: function() {
    return {
      widthProgress: 0,
    }
  },

  methods: {
    playPauseSound() {
      console.log('play');
      // get the audiofile with the correct index
      const audioFile = this.$refs.audioFile;

      // start the audio over
      audioFile.currentTime = 0;

      // if play then pause, if pause than play
      audioFile[audioFile.paused ? 'play' : 'pause']();
    },

    updateProgress(index) {

      const audioFile = this.$refs.audioFile;

      audioFile.ontimeupdate = () => {
        let percentage = (audioFile.currentTime / audioFile.duration) * 100;

        // assign percentage to widthProgress as a string
        this.widthProgress = percentage.toString() + '%';
      }

      audioFile.onended = () => {
        this.widthProgress = 0;
      }
    }
  }
}
</script>
