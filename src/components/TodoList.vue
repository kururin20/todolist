<template>
  <div>
    <div>TodoList</div>
    <div v-for="task in tasks" :key="task.name">
      <div class="task">
        <span class="state">
          <span v-if="task.state === 0">未完了：</span>
          <span v-if="task.state === 1">完了済み：</span>
        </span>
        <span class="name">名前:{{ task.name }}</span>
        <span class="limit"> 期限:{{ task.limit }} まで</span>
        <span class="state">
          <button @click="doChangeState(task)">
            <span v-if="task.state === 0">完了</span>
            <span v-if="task.state === 1">完了解除</span>
          </button>
        </span>
      </div>
    </div>
    <div>
      <label>
        名前
        <input type="text" v-model="newTaskName" />
      </label>
      <label>
        期限
        <input type="text" v-model="newTaskLimit" />
      </label>
      <button @click="addTask">add</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  data() {
    return {
      tasks: [{ name: "task1", limit: "07/03", state: 0 }],
      newTaskName: "",
      newTaskLimit: "",
      newTaskState: 0
    };
  },
  methods: {
    addTask() {
      if (this.newTaskName !== "" && this.newTaskLimit !== "") {
        this.tasks.push({ name: this.newTaskName, limit: this.newTaskLimit, state: 0 });
      }
      this.newTaskName = "";
      this.newTaskLimit = "";
      this.newTaskState = 0;
    },
    doChangeState: function(task) {
      task.state = task.state ? 0 : 1;
    }
  }
};
</script>

<style></style>
