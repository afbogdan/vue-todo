<template>
  <ul v-if="data.length">
    <TodoListItem  
        v-for="item in data" 
        :key="item.id" 
        :item="item" 
        :deleteHandler="deleteHandler"
    />
  </ul>

  <p v-else class="empty-list">There are no todos :(</p>
</template>

<script>
import TodoListItem from './TodoListItem';

export default {
    name: 'TodoList',
    components: {
        TodoListItem
    },
    props: {
        data: {
            type: Array,
            required: true
        },
        deleteHandler: {
            type: Function,
            required: true
        }
    },
    data: function() {
        return {
            isEditEnable: false
        }
    }
}
</script>

<style lang="scss" scoped>
    .box {
        box-shadow: 0px 6px 10px 0px #c6c6c6;
        background: white;
        margin: 16px 0;
        padding: 16px 32px;
    }

    ul,
    .empty-list {
        @extend .box;   
    }

    .empty-list {
        color: #626262;
        font-style: italic;
    }

    ul {
        list-style-type: none;
    }

    *::selection {
        background: none;
    }
</style>