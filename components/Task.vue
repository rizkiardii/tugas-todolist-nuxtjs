<template>
  <div class="w-full p-3 my-3 border rounded-lg">
    <div :class="`task ${task.done ? 'is-complete' : ''}`">
      <div class="content">{{ task.content }}</div>
      <div>
        <button
          @click="toggleDone"
          class="w-30 border p-2 bg-sky-300 hover:bg-sky-500 rounded-lg"
        >
          {{ task.done ? "Undo" : "Done" }}
        </button>
        <button
          @click="removeTask"
          class="w-30 border p-2 bg-red-400 hover:bg-red-500 rounded-lg"
        >
          Hapus
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["task"],
  methods: {
    toggleDone() {
      this.$store.commit("TOGGLE_TASK", this.task);
    },
    removeTask() {
      this.$store.commit("REMOVE_TASK", this.task);
    },
  },
};
</script>

<style></style>
