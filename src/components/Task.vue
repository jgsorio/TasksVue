<template>
    <div id="task">
        <form @submit.prevent="addTask">
            <input type="text" placeholder="Tarefa de Hoje?" v-model="task">
            <button>Adicionar</button>
        </form>
        <Item :tasks="tasks" @deleteTask="deleteTask"/>
        <span v-if="tasks.length">{{ tasksRemain }}</span>
    </div>
</template>

<script>
import Item from './Item.vue';

export default {
    name: 'TaskList',
    components: {
        Item
    },
    data() {
        return {
            task: '',
            tasks: []
        }
    },
    methods: {
        addTask() {
            if (!this.task.trim()) {
                alert('Digite uma tarefa');
                return;
            }

            this.tasks.push({
                id: Date.now(),
                task: this.task
            });

            this.task = '';
        },
        deleteTask(id) {
            this.tasks = this.tasks.filter(task => {
                return task.id !== id
            });
        }
    },
    computed: {
        tasksRemain() {
            return this.tasks.length > 1 ? `Restam ${this.tasks.length} tarefas para serem concluídas` : 'Resta 1 tarefa para ser concluída';
        }
    },
    watch: {
        tasks() {
            localStorage.setItem('tasks', JSON.stringify(this.tasks))
        }
    },
    mounted() {
        this.tasks = JSON.parse(localStorage.getItem('tasks')) || [];
    }
}
</script>

<style scoped>
    #task {
        max-width: 700px;
        background-color: #FFF;
        border-radius: 5px;
        padding: 20px;
        margin: 0 auto;
    }

    form {
        display: flex;
        justify-content: space-between;
    }

    form input {
        padding: 10px;
        width: 85%;
    }

    form button {
        cursor: pointer;
        background-color: #0F5959;
        color: #FFF;
        padding: 10px;
        margin-left: 10px;
        border: 0;
        border-radius: 5px;
    }

    span {
        font-size: 12.3px;
    }
</style>