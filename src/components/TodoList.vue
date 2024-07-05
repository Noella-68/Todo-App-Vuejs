<template>
    <div class="maindiv">
        <div>
            <H4>TODO LIST</H4>
        </div>
        <div class="typein">
            <input type="text"  placeholder="Type here" class="textfield" v-model="item" >
            <button v-if="!isediting" @click="addtodo" class="addbtn">Add</button>
            <button v-else @click="toupdate" class="updatebtn">Update</button>
        </div>
    </div>


    <div class="todo-table">
        <div class="table-header">
            <div class="table-cell">Task</div>
            <div class="table-cell">Status</div>
            <div class="table-cell">Update</div>
            <div class="table-cell">Action</div>
            
        </div>

        <div> 
            <ul class="list">
                <li  v-for="(x,index) in itemlist" :key="index" >
                    <div class="table-row">
                        <span class="task">{{x.task}}</span>
                        <span class="done-status task " v-if="x.isdone">Completed</span> 
                        <span class="undone-status task" v-else>Pending</span>
                        <span class="task" ><button @click="toedit(index)">Edit</button></span>
                        <span class="task" ><button @click="todelete(index)" >Delete</button></span>
                        
                    </div>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
import { ref} from 'vue';

export default {
    name: 'TodoList',
    setup()
    {   
        const takeeditedindx = ref(0)
        const isediting = ref(false)
        const item= ref('')
        const itemlist = ref([{
                task: "Do laundry",
                isdone: true
            },{
                task: "House hunt",
                isdone: false
            },

            {
                task: "Exercise for 30 min",
                isdone: true
            },


            {
                task: "Draft Business Plan",
                isdone: false
            },

            {
                task: "Read for personal growth",
                isdone: true
            }
        
        ])

        const addtodo = ()=> {
            const todo = {
                task: item.value,
                isdone: false
            }
            itemlist.value.push(todo)
        }

        const todelete = (index) => {

            itemlist.value.splice(index,1)

        }

        const toedit = (index) => {

        item.value = itemlist.value[index].task
        isediting.value= true
        takeeditedindx.value = index

        }

        const toupdate = ()=>{
            itemlist.value[takeeditedindx.value].task=item.value

            isediting.value= false
            item.value = ''
        }

        return {
                item,
                itemlist,
                addtodo,
                todelete,
                toedit,
                isediting,
                toupdate,
               }            
    } 
    
}
</script>
<style >
H4 {
    text-align: center;
}

.typein{
    text-align: center;
    
}

.textfield {
  width: 355px;
  height: 25px;
  border-radius: 5px;

}


.addbtn{
    margin: 15px;
    height: 30px;
    width: 50px;
    background-color: aqua;
    border-radius:5px ;

}



.maindiv{
    text-align: center;
}

.todo-table {
  border: 1px solid #ccc;
  border-radius: 5px;
  overflow: hidden;
}

.table-header {
  display: flex;
  flex-direction: row;
  background-color: #f0f0f0;
  padding: 10px;
}

.table-cell {
  flex: 1;
  padding: 10px;
  font-size: 18px;
  font-weight: bold;
}

.table-row {
    display: flex;
    border-top: 1px solid #ccc;
    padding: 10px;
    
   

}

.done-status
{
  color: green;
 
}

.undone-status
{
 color: red;
 
}

.task {
  flex: 1;
  padding: 10px;
  font-size: 15px;
}

.list{
list-style-type: none;
}


.updatebtn {
    margin: 15px;
    height: 30px;
    width: 70px;
    background-color: rgb(0, 255, 123);
    border-radius:5px ;

}
    
    

</style>