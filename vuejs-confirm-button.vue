<template id="vuejs-confirm-button-template">
    <span :class="styles" @click="click">{{ buttonText }}</span>
</template>

<script>
export default {
  props: ['callback', 'text', 'confirm', 'mainStyle', 'busyStyle', 'idleStyle'],

  data: function () {
    return {
      fired: false,
      busy: false
    }
  },

  computed: {
    buttonText: function () {
      return this.busy ? 'Wait' : this.fired ? this.confirm : this.text
    },

    styles: function () {
      const mainStyle = void 0 !== this.mainStyle ? this.mainStyle : 'text-button p-0'
      const idleStyle = void 0 !== this.idleStyle ? this.idleStyle : 'text-button-red'
      const busyStyle = this.busy && void 0 !== this.busyStyle ? this.busyStyle : ''

      return `${mainStyle} ${idleStyle} ${busyStyle}`
    }
  },

  methods: {
    click: function () {
      if (this.busy) {
        return
      }

      if (this.fired) {
        this.busy = true
        this.fired = false
        clearTimeout(this.timeoutId)
        this.callback()

        setTimeout(() => {
          this.busy = false
        }, 2000)
      } else {
        this.fired = true
        this.timeoutId = setTimeout(() => {
          this.fired = false
        }, 5000)
      }
    }
  },

  template: '#vuejs-confirm-button-template'
}
</script>
