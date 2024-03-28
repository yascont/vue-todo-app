<script setup props="props">
import { defineProps , ref , watch} from 'vue';

// Define props for the child component
const props = defineProps({
  tasks: Object
});


const delTask = (index)=>{
    props.tasks.splice(index, 1);
}

const handleClick = (index) =>{
    props.tasks[index].isReadOnly = !props.tasks[index].isReadOnly;
}

const handeCheck = (index) =>{
    props.tasks[index].isChecked = !props.tasks[index].isChecked;
}

</script>



<template>
    <div v-for="(task, index) in tasks" class='task'>
        <p class='check' @click="handeCheck(index)"></p>
        <input class='text' :class="{ 'checked': props.tasks[index].isChecked > 0 }" type='text' @keydown.enter="handleClick(index)" v-model="task.task" :readonly="task.isReadOnly"/>
        <p class='delete' @click="delTask(index)"></p>
        <p class='edit' @click="handleClick(index)"></p>
    </div>
</template>



<style scoped>
    .task{
    display: flex;
    min-height: 50px;
    width: 90%;
    justify-content: flex-start;
    background-color: #F1F2F1;
    margin-bottom: 6px;
    border-radius: 3px;
}


.delete{
    flex:1;
    height: 18px;
    width: 60px; 
    background-size: contain;
    background-repeat: no-repeat;
    background-image: url('https://cdn-icons-png.flaticon.com/512/860/860829.png');
    transition:  0.3s ease;
}

.edit{
    flex:1;
    height: 18px;
    width: 60px;
    background-size: contain;
    background-repeat: no-repeat;
    background-image: url('https://static-00.iconduck.com/assets.00/edit-icon-2048x2048-6svwfwto.png');
    transition:  0.3s ease;
}

.check{
    margin-left: 10px;
    flex:1;
    height: 18px;

    background-size: contain;
    background-repeat: no-repeat;
    background-image: url('https://banner2.cleanpng.com/20190218/uv/kisspng-vector-graphics-computer-icons-portable-network-gr-list-free-icons-easy-to-download-and-use-5c6b5a59549402.2235968015505393533464.jpg');
    transition:  0.3s ease;
}

.check:hover{
    cursor: pointer;
    background-image: url('https://static.vecteezy.com/system/resources/thumbnails/018/888/319/small_2x/check-mark-icon-png.png');

}

.text{
    border: none;
    background: none;
    flex: 9;
    margin-left: 5px;
}



.delete:hover{
    background-image: url('https://static.thenounproject.com/png/1064108-200.png');
    cursor: pointer;
}

.edit:hover{
    cursor: pointer;
    background-image: url('https://banner2.cleanpng.com/20191109/ijq/transparent-school-pen-icon-write-icon-tools-and-utensils-icon-5e943305c455c1.3499753315867706938042.jpg');
}

.checked{
    text-decoration: line-through;
}

</style>
