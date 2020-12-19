<template>
  <v-container
    fluid
    :class="{'pt-0': $vuetify.breakpoint.mobile}"
  >
    <v-row
      :dense="$vuetify.breakpoint.mobile"
      align="center"
    >
      <v-col cols="4">
        <buttons
          :color="'#212121'"
          :title="'7'"
          :push-value="'7'"
          @push="input"
        />
      </v-col>
      <v-col cols="4">
        <buttons
          :color="'#212121'"
          :title="'8'"
          :push-value="'8'"
          @push="input"
        />
      </v-col>
      <v-col cols="4">
        <buttons
          :color="'#212121'"
          :title="'9'"
          :push-value="'9'"
          @push="input"
        />
      </v-col>
    </v-row>
    <v-row
      :dense="$vuetify.breakpoint.mobile"
      align="center"
    >
      <v-col cols="4">
        <buttons
          :color="'#212121'"
          :title="'4'"
          :push-value="'4'"
          @push="input"
        />
      </v-col>
      <v-col cols="4">
        <buttons
          :color="'#212121'"
          :title="'5'"
          :push-value="'5'"
          @push="input"
        />
      </v-col>
      <v-col cols="4">
        <buttons
          :color="'#212121'"
          :title="'6'"
          :push-value="'6'"
          @push="input"
        />
      </v-col>
    </v-row>
    <v-row
      :dense="$vuetify.breakpoint.mobile"
      align="center"
    >
      <v-col cols="4">
        <buttons
          :color="'#212121'"
          :title="'1'"
          :push-value="'1'"
          @push="input"
        />
      </v-col>
      <v-col cols="4">
        <buttons
          :color="'#212121'"
          :title="'2'"
          :push-value="'2'"
          @push="input"
        />
      </v-col>
      <v-col cols="4">
        <buttons
          :color="'#212121'"
          :title="'3'"
          :push-value="'3'"
          @push="input"
        />
      </v-col>
    </v-row>
    <v-row
      :dense="$vuetify.breakpoint.mobile"
      align="center"
    >
      <v-col cols="4">
        <buttons
          :color="'#212121'"
          :title="'0'"
          :push-value="'0'"
          @push="input"
        />
      </v-col>
      <v-col cols="4">
        <buttons
          :color="'#212121'"
          :title="'00'"
          :push-value="'00'"
          @push="input"
        />
      </v-col>
      <v-col cols="4">
        <buttons
          :color="'#212121'"
          :title="'.'"
          :push-value="'.'"
          @push="input"
        />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Buttons from '../Buttons.vue'
export default {
  name: 'Center',
  components: { Buttons },
  methods: {
    input (val) {
      this.$emit('push-button', val)
    }
  }
}
</script>
