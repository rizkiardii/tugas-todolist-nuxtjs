<template>
  <div>
    <header class="bg-sky-500">
      <h1 class="container mx-auto py-2 text-2xl text-white">TodoList App</h1>
    </header>

    <main>
      <div class="container mx-auto">
        <div class="content w-full h-screen border rounded-lg p-3 my-3">
          <p class="p-2">Tambahkan task, di bawah ini.</p>
          <hr />
          <div class="flex flex-col my-2">
            <input
              class="border p-2 my-2 rounded-lg w-1/2 mx-auto hover:outline-sky-400 active:outline-sky-400"
              type="text"
              v-model="newTitle"
              placeholder="Judul"
              @keypress.enter="tambahTask"
            />

            <textarea
              class="border p-2 my-2 rounded-lg w-1/2 mx-auto hover:outline-sky-400 active:outline-sky-400"
              v-model="newDescription"
              placeholder="Deskripsi"
              @keypress.enter="tambahTask"
            ></textarea>

            <button
              class="w-30 border p-2 my-2 bg-sky-300 hover:bg-sky-500 rounded-lg w-1/2 mx-auto"
              @click="tambahTask"
            >
              Tambah
            </button>
          </div>
          <div class="tasks">
            <Task
              v-for="(task, i) in $store.state.tasks"
              :key="i"
              :task="task"
            />
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTitle: "",
      newDescription: "",
    };
  },

  methods: {
    tambahTask() {
      this.$store.commit("ADD_TASK", this.newTitle);
      this.newTitle = "";
      this.$store.commit("ADD_TASK", this.newDescription);
      this.newDescription = "";
    },
  },
};
</script>
