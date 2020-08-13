<template>
  <div class="todo__list-item" :class="{ 'todo__list-item--done': done }">
    <div @click="toggleDone(index)" class="todo__list-item-check">
      <svg
        width="23"
        height="18"
        viewBox="0 0 23 18"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M8.00001 13.379L3.06051 8.4395L0.939514 10.5605L8.00001 17.621L22.5605 3.0605L20.4395 0.9395L8.00001 13.379Z"
          fill="black"
        ></path>
      </svg>
    </div>
    <p>{{ text }}</p>
    <div @click="removeTask(index)" class="todo__list-item-remove">
      <svg
        width="44"
        height="44"
        viewBox="0 0 44 44"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          fill-rule="evenodd"
          clip-rule="evenodd"
          d="M27.5 8.25H35.75V11H33V35.75L30.25 38.5H11L8.25 35.75V11H5.5V8.25H13.75V5.5C13.75 4.77065 14.0397 4.07118 14.5555 3.55546C15.0712 3.03973 15.7707 2.75 16.5 2.75H24.75C25.4793 2.75 26.1788 3.03973 26.6945 3.55546C27.2103 4.07118 27.5 4.77065 27.5 5.5V8.25ZM24.75 5.5H16.5V8.25H24.75V5.5ZM11 35.75H30.25V11H11V35.75ZM16.5 13.75H13.75V33H16.5V13.75ZM19.25 13.75H22V33H19.25V13.75ZM24.75 13.75H27.5V33H24.75V13.75Z"
          fill="black"
          fill-opacity="0.5"
        ></path>
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    done: Boolean,
    text: String,
    index: Number,
  },
  methods: {
    removeTask(index) {
      if (confirm('Вы точно хотите удалить задачу?')) {
        this.$emit('onRemoveTask', index);
      }
    },
    toggleDone(index) {
      this.$emit('onToggleDone', index);
    },
  },
};
</script>
