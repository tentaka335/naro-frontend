<script setup lang="ts">
import  { computed,ref } from 'vue'
interface Task {
    isdone: boolean
    name: string
}
const tasks = ref<Task[]> (
    [
        {isdone:true,name:"部屋掃除"},
        {isdone:false,name:"ごみ捨て"}
    ]
)

const newTaskName = ref('')

const addtask = () => {
    tasks.value.push({isdone:false,name:newTaskName.value})
    newTaskName.value = ''
}

const incompleteTasks = computed(() => tasks.value.filter(task => !task.isdone))
const doneTasks = computed(() => tasks.value.filter(task => task.isdone))

</script>


<template>
    <div>ToDoList</div>
    <input v-model = newTaskName type = "text"/>
    <button @click = "addtask">タスク追加</button>
    <ul>未完タスク
        <li v-for = "task in incompleteTasks" :key = task.name>
            <input type = "checkbox" id = "checkbox" v-model = task.isdone>
            <label for ="checkbox">{{ task.name }}</label>
        </li>
    </ul>
     <ul>完了タスク
        <li v-for = "task in doneTasks" :key = task.name>
            <input type = "checkbox" id = "checkbox" v-model = task.isdone>
            <label for ="checkbox">{{ task.name }}</label>
        </li>
    </ul>
</template>


<style></style>