<template>
    <div class="flex flex-center">
        <q-btn type="a" href="#" round :color="active?'primary':'info'" text-color="white" :label="number">
            <q-badge v-if="badge" color="red" floating style="margin-top: 2.5rem">{{ badge }}</q-badge>
        </q-btn>
        <div class="q-pl-sm">{{ label }}</div>
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
