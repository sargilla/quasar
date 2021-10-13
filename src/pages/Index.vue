<template>
  <q-page class="row bg-grey-3">
    <q-card class="col-xs-9">
      <q-toolbar class="">
        <q-input
          dense
          borderless
          placeholder="buscar"
          class="full-width"
          :model-value="buscar"
        >
          <template #append>
            <q-icon name="mdi-magnify" />
          </template>
        </q-input>
      </q-toolbar>
      <TodosList bordered />
    </q-card>
    <div class="col-xs-3">
      <q-toolbar class="bg-primary">
        <CreateNewTodo
          icon="mdi-plus"
          fab
          color="secondary"
          style="margin-bottom: -42px"
          class="q-ml-md"
        />
      </q-toolbar>
    </div>
  </q-page>
</template>
<script>
import { defineComponent, ref } from "vue";
import CreateNewTodo from "components/CreateNewTodo.vue";
import TodosList from "components/TodosList.vue";
export default defineComponent({
  name: "PageIndex",
  components: { CreateNewTodo, TodosList },
  data() {
    return {
      selected: null,
      buscar: "",
    };
  },
});
</script>
