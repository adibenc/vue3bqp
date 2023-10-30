<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          Quasar App
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
          Essential Links
        </q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
		<q-tab-panels v-model="tab" animated>
		<q-tab-panel name="mails">
		  <div class="text-h6">Mails</div>
		  Lorem ipsum dolor sit amet consectetur adipisicing elit.
		</q-tab-panel>

		<q-tab-panel name="alarms">
		  <div class="text-h6">Alarms</div>
		  Lorem ipsum dolor sit amet consectetur adipisicing elit.
		</q-tab-panel>

		<q-tab-panel name="movies">
		  <div class="text-h6">Movies</div>
		  Lorem ipsum dolor sit amet consectetur adipisicing elit.
		</q-tab-panel>
	  </q-tab-panels>
      <router-view />
    </q-page-container>
	
	<q-footer bordered class="bg-grey-3 text-primary">
		<q-tabs
			v-model="tab"
			class="bg-primary text-white shadow-2"
		>
			<q-tab name="mails" label="Mails" icon="mail" />
			<q-tab name="alarms" label="Alarms" icon="alarm" />
			<q-tab name="movies" label="Movies" icon="alarm" />
		</q-tabs>
      </q-footer>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Docs',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev'
  },
  {
    title: 'Github',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: 'https://github.com/quasarframework'
  },
  {
    title: 'Discord Chat Channel',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: 'https://chat.quasar.dev'
  },
  {
    title: 'Forum',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: 'https://forum.quasar.dev'
  },
  {
    title: 'Twitter',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: 'https://twitter.quasar.dev'
  },
  {
    title: 'Facebook',
    caption: '@QuasarFramework',
    icon: 'public',
    link: 'https://facebook.quasar.dev'
  },
  {
    title: 'Quasar Awesome',
    caption: 'Community Quasar projects',
    icon: 'favorite',
    link: 'https://awesome.quasar.dev'
  }
]

export default defineComponent({
  name: 'MainLayout',
  data: function() {
	return {
		tab:[]
	};
	},

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
