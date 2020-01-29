<template>
    <div class="flex flex-center">
        <q-btn
          type="a"
          href="#"
          round
          :color="active?'primary':'info'"
          text-color="white"
          :label="number"
          size="sm"
          dense
        >
          <q-badge
            v-if="badge"
            color="red"
            class="absolute-bottom-right q-py-none"
            style="font-size: 0.4rem; right: -1rem; bottom: -0.5rem;"
          >
          {{ badge }}
          </q-badge>
        </q-btn>
        <div class="q-px-sm">{{ label }}</div>
    </div>
</template>

<script>
export default {
  name: 'RoundLabel',
  props: {
    number: Number,
    badge: String,
    label: String,
    active: Boolean
  }
}
</script>

<style lang="scss" scoped>

</style>
