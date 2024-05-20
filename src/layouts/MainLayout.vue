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
          练手广场
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        bordered
    >
      <q-list bordered separator>
        <q-item-label header>
          练手练手
        </q-item-label>

        <q-item v-for="item in drawerList" clickable v-ripple :to="item.to">
          <q-avatar :icon="item.icon"></q-avatar>
          <q-item-section>
            <q-item-label>{{ item.title }}</q-item-label>
            <q-item-label caption>{{ item.subTitle }}</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view/>
    </q-page-container>
  </q-layout>
</template>

<script setup>
import {ref} from 'vue'

defineOptions({
  name: 'MainLayout'
})

const leftDrawerOpen = ref(false)

const drawerList = ref([
  {icon: 'home', title: '首页', subTitle: '现实系统信息', to: '/'},
  {icon: 'dashboard', title: '仪表盘', subTitle: '现实系统信息', to: '/dashboard'},
  {icon: 'account_circle', title: '账号', subTitle: '当前账号信息', to: '/account'},
])

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
