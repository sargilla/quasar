<template>
  <q-btn @click="handleButtonClicked" />
</template>

<script>
import { useQuasar } from "quasar";
export default {
  name: "CreateNewTodo",
  setup() {
    const $q = useQuasar();
    const handleButtonClicked = () => {
      $q.dialog({
        title: "Create Todo",
        prompt: {
          model: "",
          type: "text",
        },
      }).onOk(createTodo);
    };
    const createTodo = (data) => {
      $q.notify({
        message: "Todo Created!",
        icon: "mdi-check",
        color: "positive",
      });
    };
    return { handleButtonClicked, createTodo };
  },
};
</script>
