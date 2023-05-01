<template>
  <q-page class="bg-grey-3 column">
    <div class="row q-pa-sm bg-primary">
      <q-input
      class="col"
      filled
      bg-color="white"
      v-model="newTask"
      @keyup.enter="addTesk()"
      placeholder="Adicionar cidade"
      dense>
     
          <q-btn 
          @click="addTesk()"
          round
          dense
          flat
          icon="add"
          />
     
      </q-input>
    </div>
    <q-list class="bg-white" separator bordered>
      <q-item
        class="bg-blue-1"
        v-for="(task, index) in tasks"
        :key="index"
        @click="task.done = !tasks.done"
        clickable
        v-ripple
      >
        <q-item-section avatar>
          <q-checkbox v-model="task.done" color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>

        <q-item-section
          @click.stop="deleteTask(index, task.title)"
          v-if="task.done"
          side
        >
          <q-btn flat round color="primary" icon="delete" dense />
        </q-item-section>
      </q-item>
    </q-list>

    <div class="no-taks absolute-center" v-if="!tasks.length">
      <q-icon
        name="check"
        size="100px"
        color="primary"
        /> 
      <div class="text-h5 text-primary text-center">
         No Task
      </div>
    
    </div>
  </q-page>
</template>

<script>
import useQuasar from "quasar/src/composables/use-quasar.js";

export default {
  data() {
    const $q = useQuasar();
    return {
      newTask: '',
      tasks: [
        {
          title: "Rio de Janeiro",
          done: false,
        },
        {
          title: "São Paulo",
          done: false,
        },
        {
          title: "Minas Gerais",
          done: false,
        },
      ],
    };
  },
  methods: {
    deleteTask(index, cidade) {
      this.$q
        .dialog({
          title: "Confirm",
          message: "Deseja Remover a cidade " + cidade + " da lista ?",
          cancel: true,
          persistent: true,
        })
        .onOk(() => {
          console.log(index);
          this.tasks.splice(index, 1);
          this.$q.notify("Removido com sucesso");
        });
    },
    addTesk(){
      this.tasks.push({
        title : this.newTask,
        done : false
      })
      this.newTask = ''
    }
  },
};
</script>

<style lang="scss">
.done {
  .q-item__labell {
    text-decoration: line-through;
    color: aliceblue;
  }
}
.no-taks {
  opacity: 0.5;
}

;
</style>
