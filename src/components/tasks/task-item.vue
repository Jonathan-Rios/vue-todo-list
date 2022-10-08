<template>
  <div>
    <v-list-item
      :class="{ 'blue lighten-4': task.completed }"
      @click="$emit('update:task', { ...task, completed: !task.completed })"
    >
      <template v-slot:default="{}">
        <v-list-item-action>
          <v-checkbox :input-value="task.completed"></v-checkbox>
        </v-list-item-action>

        <v-list-item-content>
          <v-list-item-title :class="{ 'text-decoration-line-through': task.completed }">{{
            task.title
          }}</v-list-item-title>
        </v-list-item-content>

        <v-list-item-action>
          <v-btn icon @click.stop="handleRemoveTask(task.id)">
            <v-icon color="red lighten-1">mdi-trash-can</v-icon>
          </v-btn>
        </v-list-item-action>
      </template>
    </v-list-item>
    <v-divider></v-divider>
  </div>
</template>

<script>
export default {
  props: ['task'],
  data() {
    return {
      itemStatus: false,
    };
  },
  methods: {
    handleRemoveTask(id) {
      this.$store.commit('removeTask', id);
    },
  },
};
</script>

<style></style>
