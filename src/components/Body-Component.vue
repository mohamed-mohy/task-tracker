<template>
    <div class="container">
        <div class=" box ">
            <div class="row mb-4">
            <div class="col-10 d-flex px-5">
                <h3>Task List</h3>
                
            </div>
            <div class="col-2" v-if="!updateIf">
                <button-component @toggle-show="toggleShow" :text="show ? 'Close':'Add Task'" :color="show?'danger':'success'"/>
            </div>
            </div>
                <Transition>
            <div v-show="show">
                <add-task-component @add-task="addTask"/>
            </div>
                </Transition>
            <div v-show="noData" class="text-center mt-5">
                <h3>You Don't Have Any Tasks !!</h3>
            </div>
            <div v-show="updateIf">
                <update-task-component @updated="updatedTask" :task="data" />
            </div>
            
            <tasks-page @toggle-reminder="toggleReminder" @delete-task="deleteTask" @update-task="updateTask" :tasks="tasks"/>

        </div>
    </div>
</template>
<script>
import ButtonComponent from './Button-Component.vue'
import TasksPage from './Tasks-Component.vue'
import AddTaskComponent from './AddTask-Component.vue'
import UpdateTaskComponent from './UpdateTask-Component.vue'
export default {
    name:'BodyComponent',
    components: { ButtonComponent, TasksPage ,AddTaskComponent,UpdateTaskComponent},
        data(){
        return{
        tasks:[],
        show:false,
        noData:false,
        data:{},
        updateIf:false,
        }
    },
    async created(){
        this.tasks= await this.fetchTasks();
        this.show= this.dataFn;
        this.noData=  this.dataFn;
        
    },
    methods:{
        async deleteTask(id){
            const options  = { title: 'Are you sure?',
                            text: "You won't be able to revert this!",
                            icon: 'warning',
                            showCancelButton: true,
                            confirmButtonColor: '#3085d6',
                            cancelButtonColor: '#d33',
                            confirmButtonText: 'Yes, delete it!'};  
                            this.$swal(options)
                            .then(result => {
                            if(result.isConfirmed){
                                this.tasks = this.tasks.filter(task => task.id !== id);    
                                this.$swal('Deleted!', 'Your Task has been deleted.', 'success');
                                // eslint-disable-next-line no-unused-vars
                                const response =  fetch(`https://613680a58700c50017ef55c3.mockapi.io/tasks/${id}`,{
                                    method:'DELETE',
                                })
                            }});
        },
        async toggleReminder(id){

            // eslint-disable-next-line no-unused-vars
            const response = await fetch(`https://613680a58700c50017ef55c3.mockapi.io/tasks/${id}`,{
                method:'PUT',
                body:JSON.stringify({reminder:!this.tasks.find(task => task.id === id).reminder}),
                headers:{
                    'Content-Type':'application/json'
                }
            })
            this.tasks = this.tasks.map(task => task.id === id ? {...task,reminder:!task.reminder} : task);
        },
        async addTask(task){
            const response = await fetch('https://613680a58700c50017ef55c3.mockapi.io/tasks',{
                method:'POST',
                headers:{
                    'Content-Type':'application/json'
                },
                body:JSON.stringify(task)
                })
                const data = await response.json();
            this.tasks.push(data)
            this.show=false;
            this.noData=false;
        },
        toggleShow(){
            this.show = !this.show
        },
        async fetchTasks(){
            const response = await fetch('https://613680a58700c50017ef55c3.mockapi.io/tasks')
            const data = await response.json()
            return data
        },
        async fetchTask(id){
            const response = await fetch(`https://613680a58700c50017ef55c3.mockapi.io/tasks/${id}`)
            const data = await response.json()
            return data
        },
        async updateTask(task){

            const response = await fetch(`https://613680a58700c50017ef55c3.mockapi.io/tasks/${task.id}`)
            const data = await response.json();
            this.data = data
        },
        async updatedTask(task){
            // eslint-disable-next-line no-unused-vars
            const response = await fetch(`https://613680a58700c50017ef55c3.mockapi.io/tasks/${task.id}`,{
                method:'PUT',
                body:JSON.stringify(task),
                headers:{
                    'Content-Type':'application/json'
                }
            })
            
            const data = await response.json();
            this.tasks = this.tasks.map(task => task.id === data.id ? data : task);
            this.updateIf=false;
        }
        },

    computed:{
        dataFn: function(){

            if(this.tasks.length==0){
                
                // eslint-disable-next-line vue/no-side-effects-in-computed-properties
                return true;
            }else{
                // eslint-disable-next-line vue/no-side-effects-in-computed-properties
                return false;
            }
        }
    },
    watch:{
        tasks:async function(){
            if(this.tasks.length==0){
                this.noData=true;
                this.show=true;
            }else{
                this.noData=false;
                this.show=false;
            }
            
        },
        data:function(){
            if(this.data != {}){
                this.updateIf=true;
            }else{
                this.updateIf=false;
            }
        }
    }
}
</script>
<style lang="scss" scoped>
.container{
    padding: 10px;
}
.box{
    padding: 20px;
    color: #eee
}

.v-enter-active,
.v-leave-active {
    transition: all .8s ease-in-out;
}

.v-enter-from,
.v-leave-to {
    opacity: 0;
    transform: translateY(-10px);
}


</style>