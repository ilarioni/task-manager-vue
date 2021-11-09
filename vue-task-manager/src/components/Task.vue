<template>
    <div @dblclick="$emit('toogle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">  <!-- if in task object, reminder is set to be true, it will show the border-left green style class-->
        <h3> 
            {{ task.text }} 
            <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
        </h3>
        <p> {{ task.day }} </p> 
    </div>
</template>

<script>
export default {
    name: 'Task',
    props: {
        task: Object
    },
    /*
    methods: {
        onDelete(id) {
            this.$emit('delete-task', id);
        }
    }
    */ 
}
</script>

<style scoped>
.fas {
    color: red;
}
.task {
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
}
.task:active {
  transform: scale(0.99);
}
.task.reminder {
    border-left: 5px solid green;
}

.task h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

</style>
