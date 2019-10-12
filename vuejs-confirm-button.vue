<template id="vuejs-confirm-button-template">
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
      const mainStyle = void 0 !== this.mainStyle ? this.mainStyle : 'text-button p-0'
      const confirmStyle = void 0 !== this.confirmStyle ? this.confirmStyle : ''
      const idleStyle = void 0 !== this.idleStyle ? this.idleStyle : 'text-button-red'
      const busyStyle = void 0 !== this.busyStyle ? this.busyStyle : ''

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
  },

  template: '#vuejs-confirm-button-template'
}
</script>
