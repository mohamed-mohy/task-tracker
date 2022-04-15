
<template>
    <form v-if="show" @submit="onSubmit">
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
    name:'UpdateTaskComponent',
    data() {
        return {
            text:'',
            day:'',
            reminder:false,
            id:'',
            show:false
            
        };
    },
  props:{
      task: {
          type: Object,
          required: true,
      },
  },
  computed:{
      tasks:function(){
       
                


                // eslint-disable-next-line vue/no-side-effects-in-computed-properties
                this.text = this.task.text
                // eslint-disable-next-line vue/no-side-effects-in-computed-properties
                this.day = this.task.day
                // eslint-disable-next-line vue/no-side-effects-in-computed-properties
                this.reminder = this.task.reminder
                // eslint-disable-next-line vue/no-side-effects-in-computed-properties
                this.id = this.task.id
                // eslint-disable-next-line vue/no-side-effects-in-computed-properties
                this.show = true
                return true;
                
        
      }
  },
//   watch:{
//         task:function() {
//             if(this.task != undefined)
//             {
//                 console.log(this.task)
//                 this.text = this.task.text
//                 this.day = this.task.day
//                 this.reminder = this.task.reminder
//                 this.id = this.task.id
//             }
//         },
//   },
    methods:{
       async onSubmit(e){
            e.preventDefault();
            const task = {
                id: this.id,
                text: this.text,
                day: this.day,
                reminder: this.reminder
            }
           this.$emit('updated',task);
            this.show =false
    }
        
    },
}

</script>
<style lang="">
    
</style>