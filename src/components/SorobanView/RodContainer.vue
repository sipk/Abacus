<template>
  <div class="container">
    <Pin class="container__pin"
        :isOn="isPinOn"
        :color="pinColor"
        @input="tapPin" 
      />
    <Rod class="container__rod"
        :value="value"
        :hasPoint="hasPoint"
        :beadColor="beadColor"
        @valueChanged="valueChanged"
      />
    <Finger class="container__finger"
        :isOn="isFingerOn"
        @input="tapFinger" 
      />
    <div class="container__no">
      {{digitNo}}
    </div>
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
    pinColor: String,
    beadColor: String,
    value: Number,
    hasPoint: Boolean,
    isFingerOn: Boolean
  },
  computed: {
    digitNo () {
      const max = 12
      return max - this.id
    }
  },
  methods: {
    tapPin () {
      this.$emit('tapPin', this.id);
    },
    valueChanged (value) {
      this.$emit('valueChanged', { id: this.id, value: value });
    },
    tapFinger () {
      this.$emit('tapFinger', this.id);
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
      margin-top: 6px;
    }
    .container__no {
      margin-top: 8px;
    }
</style>