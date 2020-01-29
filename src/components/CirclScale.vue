<template>
  <div class="flex flex-center">
    <div
      :class="'bg-'+circColor"
      class="row q-ma-sm flex flex-center"
      style="height: 7.4rem; width: 7.4rem; border-radius: 3.7rem"
    >
      <q-circular-progress
        show-value
        :font-size="circTextUp?'2rem':'2.5rem'"
        class="text-white"
        :value="circValue"
        size="7rem"
        :thickness="0.3"
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
    </div>
    <div class="row q-py-sm text-uppercase">
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
  }
}
</script>

<style lang="scss" scoped>

</style>
