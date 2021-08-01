<template>
  <div class="container">
    <Pin class="container__pin"
        :id="id"
        :isOn="isPinOn"
        @input="tapPin" 
      />
    <Rod class="container__rod"
        :id="id"
        :value="value"
        :hasPoint="hasPoint"
        @valueChanged="valueChanged"
      />
    <Finger class="container__finger"
        :id="id"
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
    id: Number,
    isPinOn: Boolean,
    value: Number,
    hasPoint: Boolean,
    isFingerOn: Boolean
  },
  methods: {
    tapPin (id) {
      this.$emit('tapPin', id);
    },
    valueChanged (value) {
      this.$emit('valueChanged', { id: this.id, value: value });
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