<template>
  <v-container fluid>
    <v-row>
      <v-col cols="12">
        <display
          :input-value="displayValue"
          :show="show"
          :status="operator"
        />
      </v-col>
    </v-row>
    <v-row
      v-if="$vuetify.breakpoint.mobile"
      align="stretch"
    >
      <!-- <v-col
        cols="3"
        class="ma-0 pa-0"
      >
        <left-side
          @turn-off="turnOff"
          @grand-total="grandTotal"
          @delete="deletes"
          @memory-recall="memoryRecall"
          @clear-entry="clearEntry"
          @memory-delete="memoryDelete"
          @memory-add="memoryAdd"
          @turn-on="turnOn"
        />
      </v-col> -->
      <v-col
        cols="12"
        class="ma-0 pa-0"
      >
        <left-side
          @turn-off="turnOff"
          @grand-total="grandTotal"
          @delete="deletes"
          @memory-recall="memoryRecall"
          @clear-entry="clearEntry"
          @memory-delete="memoryDelete"
          @memory-add="memoryAdd"
          @turn-on="turnOn"
        />
      </v-col>
      <!-- <v-col
          cols="4"
          class="align-stretch borders"
        >
          <right-side @push-button="input" />
        </v-col> -->
      <v-col
        cols="12"
        class="ma-0 pa-0"
      >
        <v-container
          fluid
          class="ma-0 pa-0"
        >
          <v-row
            dense
            no-gutters
          >
            <v-col
              class="mt-0 pt-0"
              cols="8"
            >
              <center @push-button="input" />
            </v-col>
            <v-col
              class="mt-0 pt-0"
              cols="4"
            >
              <right-side @push-button="input" />
            </v-col>
          </v-row>
        </v-container>
      </v-col>
    </v-row>
    <v-row
      v-else
      align="stretch"
    >
      <v-col
        cols="3"
        class="ma-0 pa-0"
      >
        <left-side
          @turn-off="turnOff"
          @grand-total="grandTotal"
          @delete="deletes"
          @memory-recall="memoryRecall"
          @clear-entry="clearEntry"
          @memory-delete="memoryDelete"
          @memory-add="memoryAdd"
          @turn-on="turnOn"
        />
      </v-col>
      <v-col
        cols="6"
        class="ma-0 pa-0"
      >
        <center @push-button="input" />
      </v-col>
      <v-col
        cols="3"
        class="ma-0 pa-0 align-self-stretch"
      >
        <right-side @push-button="input" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Center from '../components/Calc/Center.vue'
import LeftSide from '../components/Calc/LeftSide.vue'
import RightSide from '../components/Calc/RightSide.vue'
import Display from '../components/Display.vue'

export default {
  components: {
    Display,
    LeftSide,
    RightSide,
    Center
  },
  data () {
    return {
      displayValue: '0',
      show: false,
      operator: null,
      memory: [],
      prevValue: '0',
      prevType: '',
      totalArray: [],
      operators: ['multiply', 'divide', 'add', 'substract', 'square', 'percent', 'equal']
    }
  },
  methods: {
    turnOff () {
      this.show = false
      this.clear()
    },
    turnOn () {
      this.clear()
      this.show = true
    },
    clear () {
      this.totalArray = []
      this.operator = null
      this.showValue('0')
    },
    showValue (value) {
      this.displayValue = value
    },
    grandTotal () {
      let value = 0
      this.totalArray.forEach((el) => {
        value += el
      })
      this.showValue(value)
    },
    deletes () {
      const arrayString = this.displayValue.split('')
      arrayString.pop()
      const value = arrayString.join('')
      this.showValue(value)
    },
    memoryRecall () {
      if (this.memory.length > 0) {
        const value = this.memory[this.memory.length - 1]
        this.showValue(value)
      }
    },
    memoryAdd () {
      if (this.displayValue !== '0') {
        this.memory.push(this.displayValue)
      }
    },
    memoryDelete () {
      if (this.displayValue !== '0') {
        if (this.memory.includes(this.displayValue)) {
          const index = this.memory.indexOf(this.displayValue)
          this.memory.splice(index, 1)
        }
      }
    },
    clearEntry () {
      this.clear()
    },
    calculate (type = '') {
      let value = 0
      let currentValue = parseFloat(this.displayValue)
      const prevValue = parseFloat(this.prevValue)
      if (type === 'percent') {
        currentValue = prevValue * currentValue / 100
      }
      switch (this.operator) {
        case 'x':
          value = prevValue * currentValue
          break
        case ':':
          value = prevValue / currentValue
          break
        case '+':
          value = prevValue + currentValue
          break
        case '-':
          value = prevValue - currentValue
          break
        case 'sqrt':
          value = Math.sqrt(Math.abs(currentValue))
          break
        default:
          value = currentValue
          break
      }
      this.operator = '='
      this.prevType = 'calculate'
      this.totalArray.push(value)
      this.showValue(value)
    },
    input (value) {
      if (this.operators.includes(value)) {
        if (value === 'equal' || value === 'percent') {
          this.calculate(value)
        } else {
          this.calculate()
          this.prevValue = this.displayValue
          this.inputOperator(value)
        }
      } else if (value === '.') {
        if (!this.displayValue.includes('.')) {
          const val = this.displayValue + value
          this.showValue(val)
        } else if (this.prevType === 'operator' || this.prevType === 'calculate') {
          const val = '0' + value
          this.showValue(val)
        }
        this.prevType = 'decimal'
      } else if (this.displayValue === '0' || this.prevType === 'operator' || this.prevType === 'calculate') {
        this.showValue(value)
        this.prevType = 'number'
      } else {
        const val = this.displayValue + value
        this.showValue(val)
        this.prevType = 'number'
      }
    },
    inputOperator (value) {
      if (this.displayValue !== '0') {
        if (value === 'multiply') { this.operator = 'x' }
        if (value === 'divide') { this.operator = ':' }
        if (value === 'add') { this.operator = '+' }
        if (value === 'substract') { this.operator = '-' }
        if (value === 'square') { this.operator = 'sqrt' }
        this.prevType = 'operator'
      }
    }
  }
}
</script>

<style>
.borders {
  border: 1px solid black;
}
</style>
