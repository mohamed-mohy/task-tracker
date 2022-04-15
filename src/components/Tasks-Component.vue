<template>
    <TransitionGroup name="list">
        <div v-for="task in tasks" :key="task.id">
        <task-component
            @toggle-reminder="$emit('toggle-reminder', task.id)"
            @delete-task="$emit('delete-task', task.id)"
            @update-task="$emit('update-task', task)"
            :task="task" 
        />
        </div>
    </TransitionGroup>
    </template>
    <script>
    import TaskComponent from "./Task-Component.vue";
    export default {
    components: { TaskComponent },
    name: "TasksComponent",
    props: {
        tasks: {
        type: Array,
        required: true,
        },
    },
    emits: ["delete-task", "toggle-reminder","update-task"],
    };
    </script>

    <style scoped lang="scss">

    .list-enter-active,
    .list-leave-active
    {
    transition: all 0.5s ease-in-out;
    }
    .list-enter-from,
    .list-leave-to {
    opacity: 0;
    transform: translateX(30px);
    }
</style>
