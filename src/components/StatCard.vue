<template>
  <q-card class="my-card" style="height: 7rem; width: 7rem; cursor: pointer">
    <q-card-section class="q-pa-sm flex flex-center" :style="btn_left?'height: 5rem':'height: 100%'">
      <div class="row flex flex-center">
        <q-icon :name="icon" size="2rem"/>
      </div>
      <div class="row text-center text-uppercase">{{ text }}</div>
    </q-card-section>

    <q-separator v-if="btn_left" />

    <q-card-actions v-if="btn_left" align="around" class="relative-position q-my-none" >
      <div flat class="q-py-none q-my-none">
        {{ btn_left }}
        <q-badge
          v-if="icon_left"
          color="red"
          class="absolute-top-left q-py-none"
          style="font-size: 0.5rem; left: 0rem; top: 0rem;"
        >
        {{ icon_left }}
        </q-badge>
      </div>
      <div flat class="q-py-none q-my-none">
        {{ btn_right }}
        <q-badge
          v-if="icon_right"
          color="red"
          class="absolute-top-right q-py-none"
          style="font-size: 0.5rem; right: 0rem; top: 0rem;"
        >
        {{ icon_right }}
        </q-badge>
      </div>
    </q-card-actions>
  </q-card>
</template>

<script>
export default {
  name: 'StatCard',
  props: {
    btn_left: Number,
    icon_left: String,
    btn_right: Number,
    icon_right: String,
    text: String,
    icon: String
  }
}
</script>

<style lang="scss" scoped>

</style>
