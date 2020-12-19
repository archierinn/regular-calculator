<template>
  <v-btn
    :large="!$vuetify.breakpoint.mobile"
    :x-small="$vuetify.breakpoint.mobile"
    block
    :height="height"
    max-height="100%"
    class="text-center button"
    :class="{'white--text': pushValue !== '', 'button-mobile': $vuetify.breakpoint.mobile}"
    :color="color"
    @click="$emit('push', pushValue)"
  >
    <slot>
      {{ title }}
    </slot>
  </v-btn>
</template>

<script>
export default {
  name: 'Buttons',
  props: {
    title: {
      type: String,
      default: ''
    },
    color: {
      type: String,
      default: '#E0E0E0'
    },
    pushValue: {
      type: String,
      default: ''
    },
    height: {
      type: String,
      default: '5vw'
    }
  }
}
</script>

<style scoped>
.button ::v-deep span {
  font-size: 2vw;
}
.button-mobile ::v-deep span {
  font-size: auto;
}
</style>
