<template>
  <div class="container">
    <Pin class="container__pin"
        :id="pinID"
        :isOn="isPinOn"
        @input="tapPin" 
      />
    <Rod class="container__rod"
        :value="0"
        :hasPoint="hasPoint" 
      />
    <Finger class="container__finger"
        :id="fingerID"
        :isOn="isFingerOn"
        @input="tapFinger" 
      />
  </div>
</template>

<script>
import Pin from './Rod/Pin.vue'
import Rod from './Rod/Rod.vue'
import Finger from './Rod/Finger.vue'

export default {
  components: {
    Pin,
    Rod,
    Finger,
  },
  props: {
    pinID: Number,
    isPinOn: Boolean,
    hasPoint: Boolean,
    fingerID: Number,
    isFingerOn: Boolean
  },
  methods: {
    tapPin (id) {
      this.$emit('tapPin', id);
    },
    tapFinger (id) {
      this.$emit('tapFinger', id);
    }
  }
}
</script>

<style scoped>
  .container {
    /* background-color: rebeccapurple; */
  }
    .container__pin {
      margin-bottom: 7px;
    }
    .container__rod {}
    .container__finger {
      margin-top: 4px;
    }
</style>