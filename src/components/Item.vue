<template>
    <div id="item">
        <ul>
            <li v-for="task in tasks" :key="task.id">{{ task.task }} <button @click="removeItem(task.id)">Concluir</button></li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'ItemList',
    props: ['tasks'],
    methods: {
        removeItem(id) {
            this.$emit('deleteTask', id);
        }
    }
}
</script>

<style scoped>
    ul {
        margin: 0;
        padding: 10px 0;
        list-style: none;
    }

    ul li {
        display: flex;
        justify-content: space-between;
        padding: 10px 0;
        border-bottom: 1px solid #ccc;
    }

    ul li:last-child {
        border: none;
    }

    ul li button {
        cursor: pointer;
        padding: 5px;
    }
</style>