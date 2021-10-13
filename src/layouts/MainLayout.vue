<template>
  <q-layout view="hHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="mdi-menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />
        <q-toolbar-title>Todo 1.4</q-toolbar-title>
        <q-btn icon="mdi-logout" flat round />
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :width="250"
      :breakpoint="600"
      class="bg-grey-2"
    >
      <q-toolbar class="bg-primary"></q-toolbar>
      <q-item class="bg-grey-4">
        <q-item-section>Lists</q-item-section>
        <q-item-section side>
          <CreateTodoListButton flat icon="mdi-plus" round size="sm" />
        </q-item-section>
      </q-item>
      <TodoLists class="text-grey-9"> </TodoLists>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { date } from "quasar";

import { defineComponent, ref } from "vue";
import CreateTodoListButton from "components/CreateTodoListButton.vue";
import TodoLists from "components/TodoLists.vue";

export default defineComponent({
  name: "MainLayout",
  components: { CreateTodoListButton, TodoLists },
  setup() {
    const leftDrawerOpen = ref(false);

    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
  computed: {
    todayDate() {
      const timeStamp = Date.now();
      return date.formatDate(timeStamp, "DD-MM-YYYY");
    },
  },
});
</script>

<style lang="scss">
.header-img {
  opacity: 0.4;
  height: 100%;
  z-index: -1;
  filter: grayscale(100%);
}
</style>
