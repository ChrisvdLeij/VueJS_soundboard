<template>
<div class="sound-list">
  <div class="audio-item" v-for="sound in soundsJSON">
    <sound-item-content-component :sound-item="sound" />
  </div>
</div>
</template>
<script>
import soundItemContentComponent from './soundItemContentComponent.vue'

export default {
  name: 'soundItemComponent',
  components: {
    soundItemContentComponent
  },

  data: function() {
    return {
      soundsJSON: []
    }
  },

  created: function() {
    fetch("/assets/data/sounds.json")
      .then(r => r.json())
      .then(soundsJSON => {
        this.soundsJSON = soundsJSON;
      });
  }
}
</script>
