<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />


        <div class="q-px-lg q-pt-lg q-pb-md">
          <div class="text-h3">Todo</div>
          <div class="text-subtitle-1 q-py-md">{{todayDate}}</div>
        </div>
        <q-img
          src="images/fondo.jpg"
          class="header-img absolute-top">
        </q-img>
      </q-toolbar>
    </q-header>

     <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="250"
        :breakpoint="600"
      >
        <q-scroll-area style="height: calc(100% - 143px); margin-top: 143px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item to="/" exact clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="list" />
              </q-item-section>

              <q-item-section>
                Todo
              </q-item-section>
            </q-item>
            <q-item to="/help" clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="help" />
              </q-item-section>

              <q-item-section>
                Help
              </q-item-section>
            </q-item>


          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="images/fondo.jpg" style="height: 143px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="https://cdn.quasar.dev/img/boy-avatar.png">
            </q-avatar>
            <div class="text-weight-bold">Razvan Stoenescu</div>
            <div>@rstoenescu</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import { date } from 'quasar'

import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',
  setup () {
    const leftDrawerOpen = ref(false)

    return {
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  },
  computed: {
    todayDate(){
      const timeStamp = Date.now()
      return date.formatDate(timeStamp, 'DD-MM-YYYY')
    }
  }
})
</script>

<style lang="scss">
  .header-img {
    opacity: 0.4;
    height: 100%;
    z-index: -1;
    filter: grayscale(100%);
  }
</style>
