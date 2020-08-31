<template>
  <ul>
        <li v-for="item in data" v-bind:key="item.id">
            <label :for="'task' + item.id">
                <input type="checkbox" v-model="item.isDone" :id="'task' + item.id">
                {{ item.name }}
            </label>
        </li>
  </ul>
</template>

<script>
export default {
    name: 'TodoList',
    props: {
        data: Array
    }
}
</script>

<style lang="scss" scoped>
    ul {
        padding: 16px 32px;
        list-style-type: none;
        background: white;
        margin: 32px 0 16px;
        box-shadow: 0px 6px 10px 0px #c6c6c6;
        
        li {
            display: block;
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
        }
    }

    *::selection {
        background: none;
    }
</style>