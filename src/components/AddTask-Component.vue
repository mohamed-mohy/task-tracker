<template >
    <form @submit="onSubmit"  >
        <div class="m-3 col-6">
            <label for="taskName" class="form-label">Task Name:</label>
            <input type="text" v-model="text" class="form-control" id="taskName" placeholder="Add Task Name" required>
        </div>
        <div class="m-3 col-6">
            <label for="taskDate" class="form-label">Date:</label>
            <input type="date" v-model="day" class="form-control" id="taskDate" placeholder="Add Date" required>
        </div>  
        <div class="m-3 col-12">
            <div class="form-check">
                <input class="form-check-input" type="checkbox" v-model="reminder" id="Reminder" >
                <label class="form-check-label" for="Reminder">
                    Set Reminder
                </label>
        </div>
        <div class="m-3 col-4">
            <button type="submit" class="btn btn-primary px-5" id="save">Save Task</button>
        </div>
  </div>
    </form>
</template>
<script>
export default {
    name:'AddTaskComponent',
    data(){
        return{
            
                text:'',
                day:'',
                reminder:false,
        }
    },
    methods:{
        onSubmit(e){
            e.preventDefault();
            // eslint-disable-next-line no-unused-vars
            const task = {
                text: this.text,
                day: this.day,
                reminder: this.reminder
            }
            this.$emit('add-task',task);
            this.text='';
            this.day='';
            this.reminder=false;
        },
        
    },
    computed:{
    validateForm:function(){
            if
            (this.text.length > 0 && this.day.length > 0)
            {
            return  document.getElementById('save').disabled = false;
            }
            else
            {
            return document.getElementById('save').disabled = true;
            }
    }

    }
}
</script>
<style lang="scss" scoped>
    
</style>