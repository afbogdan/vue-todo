<template>
  <ul v-if="data.length">
        <li v-for="item in data" v-bind:key="item.id">
            <label :for="'task' + item.id">
                <input type="checkbox" v-model="item.isDone" :id="'task' + item.id">
                {{ item.name }}
            </label>
            <div class="actions">
                <!-- <i class="material-icons">edit</i> -->
                <i class="material-icons" @click="deleteHandler(item.id)">delete</i>
            </div>
        </li>
  </ul>

  <p v-else class="empty-list">There are no todos :(</p>
</template>

<script>
export default {
    name: 'TodoList',
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
        
        li {
            display: flex;
            align-items: center;
            justify-content: space-between;
            width: 100%;
            padding: 16px 0;
            border-bottom: 1px solid #dfdfdf;

            &:last-child {
                border-bottom: 0;
            }

            label {
                display: flex;
                cursor: pointer;

                input {
                    margin-right: 8px;
                }
            }

            .actions {
                color: #626262;

                i {
                    margin: 0 2px;
                    cursor: pointer;
                    padding: 4px;
                    border-radius: 4px;
                    transition: 0.15s;

                    &:hover {
                        color: black;
                        background: #cacaca;
                    }
                }
            }
        }
    }

    *::selection {
        background: none;
    }
</style>