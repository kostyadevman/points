<template>
  <q-layout view="lhh lpr lff">
    <q-header elevated class="glossy">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          aria-label="Menu"
          icon="menu"
        />

        <q-toolbar-title>
          Quasar App
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      bordered
      content-class="bg-grey-2"
    >

    </q-drawer>

    <q-page-container>
      <yandex-map :settings="settings"
          :coords="coords"
          @click="onClick"
        >
          <ymap-marker
            :coords="coords"
            marker-id="123"
            hint-content="some hint"
          />
        </yandex-map>
    </q-page-container>
  </q-layout>
</template>

<script>
import { yandexMap, ymapMarker  } from 'vue-yandex-maps'

export default {
  name: 'LayoutDefault',

  components: {
      yandexMap,
      ymapMarker

  },

  data () {
    return {
      leftDrawerOpen: this.$q.platform.is.desktop,
      settings: {
          apiKey: 'KEY',
          lang: 'ru_RU',
          coordorder: 'latlong',
          version: '2.1'
        },
      coords: [54, 39]
    }
  },
  methods: {
    onClick(e) {
      this.coords = e.get('coords');
    }
  }
}
</script>

<style>
</style>
