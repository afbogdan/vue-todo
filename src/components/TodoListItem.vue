<template>
    <li>
        <label :for="'task' + item.id">
            <input type="checkbox" v-model="item.isDone" :id="'task' + item.id">
            {{ item.name }}
        </label>
        <div class="actions">
            <!-- <i class="material-icons">edit</i> -->
            <i class="material-icons" @click="deleteHandler(item.id)">delete</i>
        </div>
    </li>
</template>

<script>
export default {
    name: 'TodoListItem',
    props: {
        item: {
            type: Object,
            required: true
        },
        deleteHandler: {
            type: Function,
            required: true
        }
    }
}
</script>

<style lang="scss" scoped>
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
</style>