<template >
    <div @dblclick="$emit('toggle-reminder',task.id)" :class="[task.reminder ? 'reminder':'','task']">
        <h4>{{task.text}}
            <div class="d-flex flex-column">
                <i @click="onDelete(task.id)" class="bi bi-x-lg"></i>
            <i @click="updateTask(task)" class="bi bi-pencil mt-2"></i>
            </div>
            </h4>
        <p>{{task.day}}</p>
    </div>
</template>
<script>
export default {
    name:'TaskComponent',
    props: {
        task: {
            type: Object,
            required: true
        }
    },
    methods: {
        onDelete(id){
            this.$emit('delete-task',id)
        },
        updateTask(id){
            this.$emit('update-task',id)
        }
    }
}
</script>
<style scoped lang="scss">
    .task {
    background: #eaeaea;
    border-radius: 5px;
    color: #000;
    margin: 5px;
    padding: 10px 20px;
    word-wrap: break-word;
    cursor: pointer;
    display: flex;
    justify-content: flex-start;
    flex-direction: column;
    h4 {
    display: flex;
    align-items: center;
    justify-content: space-between;
    .bi-x-lg{
        &:hover{
            color: #dc3545;
        }
    }
    .bi-pencil{
        &:hover{
            color: #007bff;
        }
    }
    }
    
}

.reminder {
    border-left: 7px solid #00ba00;
}
</style>