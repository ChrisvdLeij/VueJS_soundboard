<template>
  <div>
    <title-component title="AVROTROS Soundboard" />
    <sound-item-component/>
  </div>
</template>

<script>
import TitleComponent from './components/TitleComponent.vue';
import SoundItemComponent from './components/SoundItemComponent.vue';

export default {
  components: {
    TitleComponent,
    SoundItemComponent
  }
}
</script>
