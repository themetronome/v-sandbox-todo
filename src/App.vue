<template>
  <div id="app">
    <div class="todo">
      <div class="todo__header">
        <h4>Список задач</h4>
      </div>
      <SearchArea @onAddTask="onAddTask" />
      <div class="todo__list">
        <ListItem
          v-for="(task, index) in tasks"
          :key="index"
          :index="index"
          :text="task.text"
          :done="task.done"
          @onToggleDone="onToggleDone"
          @onRemoveTask="onRemoveTask"
        />
      </div>
    </div>
  </div>
</template>

<script>
import ListItem from './components/t-list-item';
import SearchArea from './components/t-search-area';

export default {
  name: 'App',
  data: () => ({
    tasks: [
      {
        text: 'Изучить Node.js',
        done: true,
      },
      {
        text: 'Сделать приложение на vue',
        done: false,
      },
    ],
  }),
  methods: {
    onToggleDone(index) {
      this.tasks[index].done = !this.tasks[index].done;
    },
    onRemoveTask(index) {
      this.tasks.splice(index, 1);
    },
    onAddTask(text) {
      this.tasks.push({
        text,
        done: false,
      });
    },
  },
  components: {
    ListItem,
    SearchArea,
  },
};
</script>

<style>
@import './assets/css/style.css';
</style>
