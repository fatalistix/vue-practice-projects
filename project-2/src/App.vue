<template>
  <div class="container">
    <div class="columns">
      <div class="column">
        <div class="box task-list">
          <h1>To Do</h1>
          <div class="tasks" v-for="task in tasks" :key="task.id" @dragstart="onDragStart(task)" draggable="true">
            <div v-if="task.status === 'todo'">
              {{ task.name }}
            </div>
          </div>
        </div>
      </div>
      <div class="column">
        <div class="box task-list">
          <h1>In Progress</h1>
          <div class="tasks" v-for="task in tasks" :key="task.id" @dragstart="onDragStart(task)" draggable="true">
            <div v-if="task.status === 'in-progress'">
              {{ task.name }}
            </div>
          </div>
        </div>
      </div>
      <div class="column">
        <div class="box task-list">
          <h1>Done</h1>
          <div class="tasks" v-for="task in tasks" :key="task.id" @dragstart="onDragStart(task)" draggable="true">
            <div v-if="task.status === 'done'">
              {{ task.name }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

interface Task {
  id: number;
  name: string;
  status: string;
}

export default defineComponent({
  data() {
    return {
      tasks: [
        { id: 1, name: 'Task 1', status: 'todo' },
        { id: 2, name: 'Task 2', status: 'in-progress' },
        { id: 3, name: 'Task 3', status: 'done' },
      ] as Task[],
    };
  },
  methods: {
    onDragStart(task: Task) {
      event.dataTransfer.setData('text/plain', JSON.stringify(task));
    },
  },
});
</script>

<style lang="scss">
.container {
  margin-top: 20px;
}

.box {
  margin-bottom: 20px;
}

.task-list {
  padding: 10px;
  background-color: #f5f5f5;
}

.tasks {
  margin-bottom: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  cursor: pointer;
}
</style>