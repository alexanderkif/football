<template>
  <q-page class="flex flex-center">
    <div class="row window-height window-width" style="max-width: 28rem">
      <div class="col-12 full-width">
        <div class="row">
          <div class="col-7 flex flex-center">
            <q-input rounded outlined v-model="search_text" label="Поиск" @click="search_text = 'search clicked'">
              <template v-slot:prepend>
                <q-icon name="search" @click="search_text = 'lens clicked'" />
              </template>
              <template v-slot:append>
                <q-icon name="mic_none" @click="search_text = 'mic clicked'" class="cursor-pointer" />
              </template>
            </q-input>
          </div>
          <div class="col flex flex-center">
            <q-btn type="a" href="#" flat round icon="star" text-color="positive" size="1.3rem">
              <q-icon fab name="directions_run" color="white" size="1rem" style="position: absolute" />
            </q-btn>
          </div>
          <div class="col flex flex-center">
            <q-btn type="a" href="#" flat round icon="phone" size="1.3rem"/>
          </div>
          <div class="col flex flex-center">
            <q-btn type="a" href="#" flat rounded label="Выйти" class="full-height"/>
          </div>
        </div>
        <div class="row inline justify-around q-py-md full-width">
          <round-label :number='93' label='рейтинг тренера' />
          <round-label :number='12' label='сообщения' />
          <round-label :number='54' badge='new' label='отзывы' :active='true' />
        </div>
        <div class="row bg-grey-3 flex flex-center">
          <div class="row full-width">
            <div class="col-3 flex flex-center">
              <q-img
                :src="image"
                spinner-color="white"
                style="height: 5rem; max-width: 5rem"
              />
            </div>
            <div class="trener col-9 flex flex-center">
              <div class="text-h4 q-ma-sm relative-position" style="cursor: inherit">
                {{ name }}
                <q-btn
                  outline
                  rounded
                  disable
                  color="grey-7"
                  :label="status"
                  class="absolute-bottom-right"
                  style="cursor: inherit"
                />
              </div>
            </div>
          </div>
        </div>
        <div class="row">
          <div
            class="col"
            v-for="(circ, index) in circs"
            :key="index"
          >
            <circl-scale
              :circValue="circ.circValue"
              :circMin="circ.circMin?circ.circMin:undefined"
              :circMax="circ.circMax?circ.circMax:undefined"
              :circColor="circ.circColor"
              :fontColor="circ.fontColor"
              :circTextUp="circ.circTextUp?circ.circTextUp:undefined"
              :circTextDown="circ.circTextDown"
              :circText="circ.circText"
            />
          </div>
        </div>
        <div class="row bg-grey-3 q-py-sm justify-around">
          <stat-card
            class="bg-grey-3"
            v-for="(card, index) in cards"
            :key="index"
            :icon="card.icon"
            :text="card.text"
            :btn_left="card.btn_left"
            :btn_right="card.btn_right"
            :icon_left="card.icon_left"
            :icon_right="card.icon_right"
          />
        </div>
        <div class="row bg-grey-3 justify-around q-py-md flex flex-center">
          <div>
            <q-btn
              type="a"
              href="#"
              unelevated
              rounded
              color="warning"
              label="Новые игроки от другого тренера"
              class="text-uppercase"
            />
          </div>
          <div>
            <q-btn
              type="a"
              href="#"
              unelevated
              round
              color="primary"
              icon="person_add"
              style="font-size: 1.2rem"
            />
          </div>
        </div>
        <div class="row bg-grey-3 justify-center q-pb-xl">
          <div class="row text-uppercase">Отчет селекции</div>
          <select-slider
            v-for="(slider, index) in selects"
            :key="index"
            :text="slider.text"
            :value="slider.text === 'Выполнил план' ? countPlan : slider.value"
            :max="slider.text === 'Выполнил план' ? 100 : slider.max"
            :color="slider.color"
          >
          </select-slider>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script>
import RoundLabel from '../components/RoundLabel'
import CirclScale from '../components/CirclScale'
import StatCard from '../components/StatCard'
import SelectSlider from '../components/SelectSlider'

export default {
  name: 'PageIndex',
  components: {
    RoundLabel,
    CirclScale,
    StatCard,
    SelectSlider
  },
  computed: {
    countPlan () {
      let procents = 0
      for (let i = 1; i < this.selects.length; i++) {
        procents += Math.floor(this.selects[i].value * 100 / this.selects[i].max)
      }
      return Math.round(procents / 3)
    }
  },
  data () {
    return {
      search_text: '',
      reiting: 93,
      reitingBadge: 4,
      image: 'statics/fci.png',
      name: 'Сергей Сергеевич Никитин',
      status: 'ТРЕНЕР',
      selects: [
        {
          text: 'Выполнил план',
          color: 'negative'
        },
        {
          text: 'Прозвонил',
          value: 17,
          max: 35,
          color: 'secondary'
        },
        {
          text: 'Пригласил',
          value: 14,
          max: 20,
          color: 'warning'
        },
        {
          text: 'Пришли',
          value: 2,
          max: 5,
          color: 'positive'
        }
      ],
      circs: [
        {
          circValue: 6,
          circMin: 0,
          circMax: 15,
          circColor: 'positive',
          fontColor: 'white',
          circTextUp: 'групп / детей',
          circTextDown: 'количество',
          circText: 'Ваши группы'
        },
        {
          circValue: 13,
          circColor: 'warning',
          fontColor: 'grey-10',
          circTextDown: 'человек',
          circText: 'оплаты'
        },
        {
          circValue: 23,
          circColor: 'negative',
          fontColor: 'white',
          circTextDown: 'количество',
          circText: 'Задачи'
        }
      ],
      cards: [
        {
          icon: 'business_center',
          text: 'Обучение',
          btn_left: 123,
          btn_right: 7,
          icon_right: 'new'
        },
        {
          icon: 'money',
          text: 'Финансовый отчет'
        },
        {
          icon: 'library_books',
          text: 'Сдача отчета'
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
