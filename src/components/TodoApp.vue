<template >
    <div>
<body class="h-screen  overflow-hidden flex items-center justify-center" style="background: #edf2f7;">
    <div class="h-300  w-full flex items-center justify-center bg-teal-lightest font-sans">
	<div class="bg-white rounded shadow p-10 m-8 w-full lg:w-3/4 lg:max-w-lg">
        <div class="mb-5">
            <h1 class="text-grey-darkest">Todo List</h1>
            <div class="flex mt-4">
                <input @keyup.enter="submbiTastks" v-model="task" class="shadow appearance-none border rounded w-full py-2 px-3 mr-4 text-grey-darker" placeholder="Add Todo">
                <button @click ="submbiTastks" class="flex-no-shrink p-2 border-2 rounded text-teal border-teal hover:text-white hover:bg-teal">Add</button>
            </div>
        </div>
        <div v-for="(task , index) in tasks" :key="index">
            <div class="flex mb-4 items-center">
                <p class="w-full text-grey-darkest">{{task.name}}</p>
                <button @click="changeState(index)" class="flex-no-shrink p-2 ml-4 mr-2 border-2 rounded hover:text-white text-green border-green hover:bg-green">{{task.status}}</button>
                <button @click="updatedTask(index)" class="flex-no-shrink p-2 ml-2 border-2 rounded text-green border-green hover:text-white hover:bg-green">Update</button>
                <button @click="removeTask(index)"  class="flex-no-shrink p-2 ml-2 border-2 rounded text-red border-red hover:text-white hover:bg-red">Remove</button>
                
            </div>
          	<div class="flex mb-4 items-center">
                <p class="w-full line-through text-green">Submit Todo App Component to Tailwind Components</p>
                <button class="flex-no-shrink p-2 ml-4 mr-2 border-2 rounded hover:text-white text-grey border-grey hover:bg-grey">Not Done</button>
                <!-- <button @click="removeTask" class="flex-no-shrink p-2 ml-2 border-2 rounded text-red border-red hover:text-white hover:bg-red">Remove</button> -->
            </div>
        </div>
    </div>
</div>
</body>
    </div>
</template>
<script>
export default {
    name : "TodoApp",

    data() {
        return {
            task:'',
            editTask: null,
            availabeStatus : ["to-do", "in-progress", "finished"],
            tasks : [
                {
                    name : "La meilleure to do list",
                    status :'Done'
                },
                 {
                    name : "Eat 1kg chocolate in 5s",
                    status :'Done'
                },
                 {
                    name : "Eat 1kg totalmem in 2min",
                    status :'Done'
                }
            ]
        }
    },
    methods : {
        submbiTastks()
        {
            // console.log(this.task) 
         if (this.task.length === 0) return; 

        if (this.editTask === null) 
        {
            this.tasks.push(
                    {
                        name :this.task,
                        status :'Done'
                    } )
                    this.task=''
        }else{
            this.tasks[this.editTask].name = this.task;
            this.editTask= null;
            this.task=''
        }
       
            

        },
        removeTask(index)
        {
           this.tasks.splice(index,1)  
            // console.log(index)     
        },
        updatedTask(index)
        {
            console.log(this.tasks[index])
            this.task=this.tasks[index].name
            //  submbiTastks()
            this.editTask= index

        },
          changeState(index)
        {
            // console.log(this.availabeStatus.indexof(this.tasks[index].status))
         let newindex= this.availabeStatus.indexOf(this.tasks[index].status);
        //  console.log(newindex)
         if (++newindex>2) newindex =0;

         this.tasks[index].status= this.availabeStatus[newindex];
        }
    }
}
</script>
<style >
    
</style>