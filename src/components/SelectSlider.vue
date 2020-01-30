<template>
  <div class="q-px-lg q-py-sm col-12">
    <div class="row full-width justify-between">
      <div>
        {{ text }}
      </div>
      <div>
        {{ value }}
      </div>
    </div>
    <div
      class="row relative-position bg-grey-5"
      style="height: 0.6rem; width: 100%; border-radius: 0.3rem"
    >
      <div
        :class="'value absolute bg-' + color"
        :style="'height: inherit; border-radius: inherit'"
      >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SelectSlider',
  props: {
    text: String,
    value: Number,
    max: Number,
    color: String
  },
  mounted () {
    const value = this.$el.getElementsByClassName('value')[0]
    const width = Math.floor(this.value * 100 / this.max)
    value.style.width = `${width > 100 ? 100 : width}%`
  }
}
</script>

<style lang="scss" scoped>

</style>
