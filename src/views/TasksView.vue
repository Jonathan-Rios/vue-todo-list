<template>
  <div>
    <v-col cols="12">
      <v-text-field
        label="Qual a sua tarefa?"
        v-model="taskInput"
        outlined
        @keyup.enter="handleAddTask"
      ></v-text-field>
    </v-col>
    <v-list flat subheader>
      <v-list-item-group multiple active-class="">
        <div v-for="(task, index) in $store.state.tasks" :key="index">
          <TaskItem :task.sync="$store.state.tasks[index]" />
        </div>
      </v-list-item-group>
    </v-list>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import TaskItem from '../components/tasks/task-item.vue';

export default Vue.extend({
  name: 'TasksView',

  components: { TaskItem },
  data() {
    return {
      taskInput: null,
    };
  },
  methods: {
    handleAddTask() {
      this.$store.commit('addTask', this.taskInput);
      this.taskInput = null;
    },
  },
});
</script>
