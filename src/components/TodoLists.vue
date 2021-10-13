<template>
  <q-list>
    <q-item to="/" exact clickable v-ripple>
      <q-item-section avatar>
        <q-icon name="mdi-clipboard-list" />
      </q-item-section>

      <q-item-section> Todo </q-item-section>
    </q-item>
    <q-item to="/shopping" exact clickable v-ripple>
      <q-item-section avatar>
        <q-icon name="mdi-shopping" />
      </q-item-section>

      <q-item-section> Shopping List </q-item-section>
      <q-item-section side>12</q-item-section>
    </q-item>
    <q-item to="/help" clickable v-ripple>
      <q-item-section avatar>
        <q-icon name="mdi-help" />
      </q-item-section>

      <q-item-section> Helps to user </q-item-section>
    </q-item>
  </q-list>
</template>

<script>
export default {
  // name: 'ComponentName',
  setup() {
    return {};
  },
};
</script>
