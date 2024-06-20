<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />

        <q-toolbar-title class="absolute-center">
          Awesome Todo
        </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer :breakpoint="768" v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header>
          Navigation
        </q-item-label>
        <q-item v-for="item in navItems" :key="item.name" :to="item.path" clickable exact>
          <q-item-section avatar>
            <q-icon :name="item.icon" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{ item.label }}</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer elevated>
      <q-tabs>
        <q-route-tab exact v-for="item in navItems" :key="item.name" :to="item.path" :name="item.name" :icon="item.icon"
          :label="item.label" />
      </q-tabs>
    </q-footer>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',

  components: {
  },

  setup() {
    const leftDrawerOpen = ref(false)
    const navItems = ref([
      {
        name: 'todo',
        label: 'Todo',
        icon: 'list',
        path: '/',
      },
      {
        name: 'settings',
        label: 'Settings',
        icon: 'settings',
        path: '/settings',
      }
    ])

    return {
      leftDrawerOpen,
      navItems,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>

<style>
@media screen and (min-width: 768px) {
  .q-footer {
    display: none;
  }
}
</style>
