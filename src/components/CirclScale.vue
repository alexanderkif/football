<template>
  <div class="flex flex-center">
    <div
      :class="'bg-'+circColor"
      class="row q-my-sm flex flex-center"
      style="height: 7rem; width: 7rem; border-radius: 3.5rem"
    >
      <q-circular-progress
        show-value
        :font-size="circTextUp?'2rem':'2.5rem'"
        class="text-white"
        :value="circValue"
        size="6.6rem"
        :thickness="0.2"
        color="white"
        :track-color="circColor"
        :min="circMin||0"
        :max="circMax||100"
      >
        <div :class="'text-'+fontColor">
          <div v-if="circTextUp" class="row flex flex-center" style="font-size: 0.55rem">
            {{ circTextUp }}
          </div>
          <div class="row q-mb-xs flex flex-center" style="border-bottom: 1px solid">
            {{ circValue + (circMax?'/'+circMax:'') }}
          </div>
          <div class="row q-my-xs text-uppercase flex flex-center" style="font-size: 0.55rem">
            {{ circTextDown }}
          </div>
        </div>
      </q-circular-progress>
      <q-circular-progress
        :font-size="circTextUp?'2rem':'2.5rem'"
        class="circltemplate absolute text-primary"
        :value="circValue"
        size="6.6rem"
        :thickness="0.2"
        :color="circColor"
        track-color="transparent"
        :min="circMin||0"
        :max="circMax||100"
      >
      </q-circular-progress>
    </div>
    <div class="row q-pb-sm text-uppercase">
      {{ circText }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'CirclScale',
  props: {
    circValue: Number,
    circMin: Number,
    circMax: Number,
    circColor: String,
    fontColor: String,
    circTextUp: String,
    circTextDown: String,
    circText: String
  },
  mounted () {
    const qicon = this.$el.getElementsByClassName('circltemplate')[0]
    const circle = qicon.getElementsByTagName('circle')[0]
    circle.setAttribute('stroke-dasharray', '4,4')
  }
}
</script>

<style lang="scss" scoped>

</style>
