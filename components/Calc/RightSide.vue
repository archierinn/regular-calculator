<template>
  <v-container
    fluid
    :class="{'pt-0': $vuetify.breakpoint.mobile}"
  >
    <!-- <div class="d-flex flex-column borders">
      <div class="flex-fill">
        ABC
      </div>
      <div>DEF</div>
    </div> -->
    <v-row :dense="$vuetify.breakpoint.mobile">
      <v-col cols="6">
        <buttons @push="$emit('push-button', 'multiply')">
          &times;
        </buttons>
      </v-col>
      <v-col cols="6">
        <buttons @push="$emit('push-button', 'divide')">
          &divide;
        </buttons>
      </v-col>
    </v-row>
    <v-row :dense="$vuetify.breakpoint.mobile">
      <v-col cols="6">
        <buttons @push="$emit('push-button', 'multiply')">
          &times;
        </buttons>
      </v-col>
      <v-col cols="6">
        <buttons @push="$emit('push-button', 'divide')">
          &divide;
        </buttons>
      </v-col>
    </v-row>
    <v-row
      :dense="$vuetify.breakpoint.mobile"
      align="stretch"
    >
      <v-col cols="6">
        <buttons
          :height="'100%'"
          @push="$emit('push-button', 'add')"
        >
          &plus;
        </buttons>
      </v-col>
      <v-col
        cols="6"
        class="d-flex flex-column justify-space-between"
      >
        <div class="ma-0 pa-0">
          <buttons @push="$emit('push-button', 'percent')">
            &percnt;
          </buttons>
        </div>
        <div
          class="ma-0 pa-0"
          :class="{'mt-5': !$vuetify.breakpoint.mobile, 'mt-2': $vuetify.breakpoint.mobile}"
        >
          <buttons @push="$emit('push-button', 'equal')">
            &equals;
          </buttons>
        </div>
      </v-col>
    </v-row>
  </v-container>
  <!-- <v-container fluid>
    <v-row align="center">
      <v-col cols="6">
        <buttons @push="$emit('push-button', 'multiply')">
          &times;
        </buttons>
      </v-col>
      <v-col cols="6">
        <buttons @push="$emit('push-button', 'divide')">
          &divide;
        </buttons>
      </v-col>
    </v-row>
    <v-row
      align="center"
      class="borders"
    >
      <v-col cols="6">
        <buttons @push="$emit('push-button', 'substract')">
          &minus;
        </buttons>
      </v-col>
      <v-col cols="6">
        <buttons @push="$emit('push-button', 'square')">
          &radic;
        </buttons>
      </v-col>
    </v-row>
    <v-row
      align="stretch"
      class="flex-grow-1 borders"
    >
      <v-col cols="6">
        <buttons
          :height="'100%'"
          @push="$emit('push-button', 'add')"
        >
          &plus;
        </buttons>
      </v-col>
      <v-col
        cols="6"
        class="d-flex flex-column justify-space-between"
      >
        <div class="ma-0 pa-0">
          <buttons @push="$emit('push-button', 'percent')">
            &percnt;
          </buttons>
        </div>
        <div class="ma-0 pa-0">
          <buttons @push="$emit('push-button', 'equal')">
            &equals;
          </buttons>
        </div>
      </v-col>
    </v-row>
  </v-container> -->
</template>

<script>
// import Buttons from '../Buttons.vue'
export default {
  name: 'RightSide',
  components: {
    // Buttons
  }
}
</script>
