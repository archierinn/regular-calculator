<template>
  <v-container fluid>
    <v-row align="center">
      <v-col cols="6">
        <buttons
          :color="'error'"
          :title="'Off'"
          @push="$emit('turn-off')"
        />
      </v-col>
      <v-col cols="6">
        <buttons
          :title="'GT'"
          @push="$emit('grand-total')"
        />
      </v-col>
    </v-row>
    <v-row align="center">
      <v-col cols="6">
        <buttons @push="$emit('delete')">
          <v-icon :x-small="$vuetify.breakpoint.mobile">
            mdi-arrow-right
          </v-icon>
        </buttons>
      </v-col>
      <v-col cols="6">
        <buttons
          :title="'MR'"
          @push="$emit('memory-recall')"
        />
      </v-col>
    </v-row>
    <v-row align="center">
      <v-col cols="6">
        <buttons
          :title="'CE'"
          @push="$emit('clear-entry')"
        />
      </v-col>
      <v-col cols="6">
        <buttons
          :title="'M-'"
          @push="$emit('memory-delete')"
        />
      </v-col>
    </v-row>
    <v-row align="center">
      <v-col cols="6">
        <buttons
          :color="'error'"
          :title="'On'"
          @push="$emit('turn-on')"
        />
      </v-col>
      <v-col cols="6">
        <buttons
          :title="'M+'"
          @push="$emit('memory-add')"
        />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Buttons from '../Buttons.vue'
export default {
  name: 'LeftSide',
  components: {
    Buttons
  }
}
</script>
