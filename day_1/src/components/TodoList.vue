<script setup>
import { ref,computed } from 'vue';

const task=ref([]);
const newtask=ref('');
const warning =ref('');

function addTask(){
    if(newtask.value.trim()!==''){
        const id =Date.now();
        task.value.push({id:id,title:newtask.value,done:false});
        newtask.value='';
        warning.value='';
    }else{
        warning.value='Isi tasknya dulu yaa';
    }
}

function removeTask(id){
    const idx = task.value.findIndex(t=>t.id===id);
    if(idx>-1){
        task.value.splice(idx,1);
    }
}

function toggleDone(id){
    const t = task.value.find(t=>t.id===id);
    if(t){
        t.done=!t.done;
    }
}

const ActiveTask=computed(()=> task.value.filter(t=>!t.done).length);

const orderedTasks=computed(()=>{
    const doneTask=task.value.filter(t=>t.done);
    const notDoneTask=task.value.filter(t=>!t.done);
    return [...notDoneTask,...doneTask];
});

</script>

<template>
    <div>
        
        <div>
            <h2>Todo List</h2>
            <p>Active Taks : {{ ActiveTask }}</p>
        </div>
        
        <div>
            <input type="text" v-model="newtask" @keyup.enter="addTask" placeholder="Isi Taks">
            <button @click="addTask">Tambah</button>
            <p style="color:red">{{warning}}</p>
        </div>

        <div>
            <div v-for="task in orderedTasks" :key="task.id">
                <label>
                    <input type="checkbox" :checked="task.done" @change="toggleDone(task.id)">
                    <span :class="{ completed: task.done }">{{ task.title }}</span>
                </label>

            </div>
        </div>

        <div v-if="task.length===0">
            <p>Tidak ada task</p>
        </div>

    </div>
</template>

<style scoped>
.completed{ text-decoration:line-through;color:#9aa3ab }
</style>