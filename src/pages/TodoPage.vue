<template>
  <q-page padding>
    <div v-if="tasks.length">
      <q-list separator bordered>
        <q-item v-for="task in tasks" :key="task.id" tag="label" v-ripple
          :class="task.completed ? 'bg-green-1' : 'bg-orange-1'">
          <q-item-section avatar top>
            <q-checkbox v-model="task.completed" />
          </q-item-section>
          <q-item-section>
            <q-item-label :class="{ 'text-strikethrough': task.completed }">{{ task.name }}</q-item-label>
            <q-item-label caption>{{ task.description }}</q-item-label>
          </q-item-section>
          <q-item-section side>
            <div class="row">
              <div class="column justify-center">
                <q-item-label caption class="row justify-end">
                  {{ task.dueDate }}
                </q-item-label>
                <q-item-label caption class="row justify-end">
                  <small>{{ task.dueTime }}</small>
                </q-item-label>
              </div>
              <div class="column justify-center q-ml-sm">
                <q-icon name="event" size="sm" />
              </div>
            </div>
          </q-item-section>

        </q-item>
      </q-list>
    </div>
    <div v-else>No tasks available</div>
  </q-page>
</template>

<script>
import { defineComponent, ref, computed } from 'vue'

export default defineComponent({
  name: 'TodoPage',
  components: {
  },
  data() {
    return {
      model: false,
      tasks: [
        {
          id: 1,
          name: 'Task 1',
          description: 'Task description 1',
          completed: false,
          dueDate: '2024-06-19',
          dueTime: '12:30:00',

        },
        {
          id: 2,
          name: 'Task 2',
          description: 'Task description 2',
          completed: false,
          dueDate: '2024-06-20',
          dueTime: '19:30:00',
        },
        {
          id: 3,
          name: 'Task 3',
          description: 'Task description 3',
          completed: false,
          dueDate: '2024-06-25',
          dueTime: '14:30:00',
        }
      ]
    }
  },
  methods: {
    deleteTask(i) {
      console.log('delete')
      this.tasks.splice(i, 1)
    }
  }
});
</script>
