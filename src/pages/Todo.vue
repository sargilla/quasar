<template>
  <q-page class="bg-grey-3 column">
    <div class="row q-pa-sm bg-primary">
      <q-input
        v-model="newTask"
        placeholder="Ingresar una tarea "
        bg-color="white"
        dense
        square
        filled
        class="col"
        @keyup.enter="addTask">
        <template v-slot:append>
          <q-btn round dense flat icon="add" @click.stop="addTask" />
        </template>
      </q-input>
    </div>
    <q-list class="bg-white" separator bordered>
        <q-item
        v-for="(task, index) in tasks"
        :key="index"
        v-ripple
        clickable
        @click="task.done = !task.done"
        :class="{'done':task.done}">
        <q-item-section avatar>
            <q-checkbox v-model="task.done" color="primary" class="no-pointer-events"/>
        </q-item-section>
        <q-item-section>
            <q-item-label v-text="task.title"/>
        </q-item-section>
        <q-item-section v-if="task.done" avatar>
            <q-btn
              flat
              round
              color="primary"
              icon="delete"
              dense
              @click.stop="deleteTask(index)"/>
        </q-item-section>
        </q-item>
    </q-list>
    <div v-show="!tasks.length" class="no-tasks absolute-center">
      <q-icon name="check" size="100px" color="primary"></q-icon>
      <div class="text-h5 text-primary text-center">No hay Tareas</div>
    </div>
  </q-page>
</template>

<script>
import { defineComponent, ref } from 'vue';
export default defineComponent({
  name: 'TodoPage',
  data() {
    return {
      newTask:"",
      tasks:[]
    }
  },
  methods: {
    deleteTask (index) {
      this.$q.dialog({
        title: 'Confirmar',
        message: 'Quieres borrar este task?',
        cancel: true,
        persistent: true
      }).onOk(() => {
        this.$q.notify({position:'bottom-right',message: 'Borraste esta tarea!'})
        this.tasks.splice(index,1)
      })
    },
    addTask(){
      this.tasks.push({title:this.newTask,done:false});
      this.newTask=''
      this.$q.notify({position:'bottom-right',message: 'Agregaste una tarea!'})
    }
  },
})
</script>

<style lang="scss">
.done {
  .q-item__label {
    text-decoration: line-through;
    color:#bbb;
  }
}
</style>
