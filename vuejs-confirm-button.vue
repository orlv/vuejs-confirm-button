<template>
    <span :class="styles" @click="click">{{ buttonText }}</span>
</template>

<script>
export default {
  props: ['callback', 'text', 'confirm', 'mainStyle', 'confirmStyle', 'busyStyle', 'idleStyle', 'confirmTimeout', 'busyTimeout'],

  data () {
    return {
      fired: false,
      busy: false
    }
  },

  computed: {
    buttonText () {
      return this.busy ? 'Wait' : this.fired ? this.confirm : this.text
    },

    styles () {
      const mainStyle = this.mainStyle !== undefined ? this.mainStyle : 'text-button p-0'
      const confirmStyle = this.confirmStyle !== undefined ? this.confirmStyle : ''
      const idleStyle = this.idleStyle !== undefined ? this.idleStyle : 'text-button-red'
      const busyStyle = this.busyStyle !== undefined ? this.busyStyle : ''

      return `${mainStyle} ${this.fired ? confirmStyle : this.busy ? busyStyle : idleStyle}`
    }
  },

  methods: {
    click () {
      if (!this.busy) {
        if (this.fired) {
          this.busy = true
          this.fired = false
          clearTimeout(this.timeoutId)
          this.callback()

          setTimeout(() => {
            this.busy = false
          }, typeof this.confirmTimeout === 'number' ? this.confirmTimeout : 2000)
        } else {
          this.fired = true
          this.timeoutId = setTimeout(() => {
            this.fired = false
          }, typeof this.busyTimeout === 'number' ? this.busyTimeout : 5000)
        }
      }
    }
  }
}
</script>
