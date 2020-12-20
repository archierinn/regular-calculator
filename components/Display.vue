<template>
  <v-layout>
    <v-text-field
      v-if="show"
      v-model="inputValue"
      hide-details="auto"
      outlined
      solo
      flat
      reverse
      readonly
      class="display"
      max-height="10vw"
      height="10vw"
    >
      <template v-slot:append>
        <span
          v-if="show"
          class="status-text"
        >{{ status }}</span>
      </template>
    </v-text-field>
    <v-text-field
      v-else
      hide-details="auto"
      outlined
      solo
      flat
      reverse
      readonly
      class="display"
      max-height="8vw"
      height="10vw"
      value=""
    />
  </v-layout>
</template>

<script>
export default {
  name: 'Display',
  props: {
    inputValue: {
      type: String,
      default: '0'
    },
    show: {
      type: Boolean,
      default: false
    },
    status: {
      type: String,
      default: null
    }
  }
}
</script>

<style scoped>
.display,
.status-text {
  font-family: "DigitalNormal-xO6j";
}
.status-text {
  font-size: 6vw;
}
.display ::v-deep input {
  font-size: 8vw !important;
  max-height: 10vw !important;
}
</style>
