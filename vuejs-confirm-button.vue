<template id="vuejs-confirm-button-template">
    <span class="text-button p-0" :class="{'text-button-red': !busy }" @click="click">{{ buttonText }}</span>
</template>

<script>
export default {
  props: ['callback', 'text', 'confirm'],

  data: function () {
    return {
      fired: false,
      busy: false
    }
  },

  computed: {
    buttonText: function () {
      return this.busy ? 'Wait' : this.fired ? this.confirm : this.text
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
