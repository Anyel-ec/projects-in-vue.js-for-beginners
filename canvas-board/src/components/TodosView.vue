<script setup>
import { reactive } from 'vue';

let boards = reactive([
    {
        id: crypto.randomUUID(),
        name: 'board 1',
        items: [
            {
                id: crypto.randomUUID(),
                title: "Feature of files",
            },
            {
                id: crypto.randomUUID(),
                title: "Resolver bug",
            },

        ],
    },
    {
        id: crypto.randomUUID(),
        name: 'board 2',
        items: [
            {
                id: crypto.randomUUID(),
                title: "Send Report",
            },
            {
                id: crypto.randomUUID(),
                title: "Code review",
            },

        ],
    },


])
function handleNewItem(item) {
    boards[0].items.push({
        id: crypto.randomUUID(),
        title: item,
    })
}
</script>



<template>
    <nav>
        <ul>
            <li><a href="#">Create board</a></li>

        </ul>
    </nav>
<div class="boards-container">
    <div class="boards">
        <div class="board" v-for="board in boards" :key="board.id">
            <div>{{ board.name }}</div>
            <InputNew @on-new-items="handleNewItem" />
            <div class="items">
                <div class="item" v-for=" item in board.items" :key="item.id">
                    {{ item.title }}
                </div>
            </div>

        </div>
    </div>
</div>
</template>

<style scoped>
.boards{
    display: flex;
    gap: 10px;
    margin: 5px;
}
.board{
    background-color: rgb(51, 51, 51);
}
.item{
    background-color: rgb(44, 44, 44);
    padding: 10px;
    box-sizing: border-box;
}

</style>
