<template>
  <div>
    <h5>{{ task.title }}</h5>
    <h6 class="text-muted">{{ deadline }}</h6>
    <div class="clearfix">
      <div class="pull-right">
        <button class="btn btn-outline-success" @click="startEditing()">
          <i class="fa fa-edit"></i>
        </button>
        <button class="btn btn-outline-secondary" @click="deleteTask()">
          <i class="fa fa-trash"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import moment from 'moment';

export default {
  props: ['task'],
  computed: {
    deadline() {
      if (!this.task.deadline) {
        return 'No deadline';
      }
      const deadline = moment(this.task.deadline).format('yyyy/MM/DD');
      return `by ${deadline}`;
    },
  },
  methods: {
    startEditing() {
      this.$emit('start-editing');
    },
    deleteTask() {
      this.$emit('delete-task');
    },
  },
};
</script>
