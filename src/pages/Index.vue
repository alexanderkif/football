<template>
  <q-page class="flex flex-center">
    <div class="row window-height window-width" style="max-width: 28rem">
      <div class="column full-width">
        <div class="row">
          <div class="col-8" style="height: 4rem; padding: 0.25rem 0">
            <div class="flex flex-center" input-style="height: 3rem">
              <q-input rounded outlined v-model="search_text" label="Поиск" @click="search_text = 'search clicked'">
                <template v-slot:prepend>
                  <q-icon name="search" @click="search_text = 'lens clicked'" />
                </template>
                <template v-slot:append>
                  <q-icon name="mic_none" @click="search_text = 'mic clicked'" class="cursor-pointer" />
                </template>
              </q-input>
            </div>
          </div>
          <div class="col-1 flex flex-center">
            <q-btn type="a" href="#" flat round icon="star" text-color="positive" size="1.3rem">
              <q-icon fab name="directions_run" color="white" size="1rem" style="position: absolute" />
            </q-btn>
          </div>
          <div class="col-1 flex flex-center">
            <q-btn type="a" href="#" flat round icon="phone"/>
          </div>
          <div class="col-2 flex flex-center">
            <q-btn type="a" href="#" flat label="Выйти"/>
          </div>
        </div>
        <div class="row inline justify-between" style="height: 3rem">
            <round-label :number='93' label='рейтинг тренера'></round-label>
            <round-label :number='12' label='сообщения'></round-label>
            <round-label :number='54' badge='new' label='отзывы' active='true'></round-label>
        </div>
        <div class="bg-pink-5" style="height: 6.5rem">
        </div>
        <div class="bg-pink-3" style="height: 12.5rem">
          .col-8
        </div>
        <div class="bg-pink-5" style="height: 8.5rem">
          .col
        </div>
        <div class="bg-pink-3" style="height: 6rem">
          .col-8
        </div>
        <div class="bg-pink-5" style="height: 14.5rem">
          .col-4
        </div>
      </div>
    </div>
  </q-page>
</template>

<script>
import RoundLabel from '../components/RoundLabel'

export default {
  name: 'PageIndex',
  components: {
    RoundLabel
  },
  data () {
    return {
      search_text: '',
      reiting: 93,
      reitingBadge: 4
    }
  }
}
</script>
