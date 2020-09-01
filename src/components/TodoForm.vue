<template>
  <form class="box" @submit.prevent="triggerHandler" v-if="!disabled">
      <label for="addTask">{{ label }}</label>
      <input id="addTask" type="text" v-model="taskName">
      <input type="submit" :value="submitText">
  </form>

  <p v-else class="box alert"><strong>Cannot more than the limit :(</strong></p>
</template>

<script>
export default {
    name: 'TodoForm',
    props: {
        label: {
            type: String,
            required: true
        },
        submitText: {
            type: String,
            required: true
        },
        submitHandler: {
            type: Function,
            required: true
        },
        disabled: {
            type: Boolean,
            required: true
        }
    },
    data: function() {
        return {
            taskName: ''
        }
    },
    methods: {
        triggerHandler: function() {
            this.submitHandler(this.taskName);
            this.taskName = '';
        }
    }
}
</script>

<style lang="scss" scoped>
    form {
        > * {
            display: block;
        }

        label {
            font-size: 0.9rem;
        }

        input[type=text] {
            width: 100%;
            outline: none;
            border-width: 0 0 2px 0;
            border-style: solid;
            border-color: gray;
            padding: 4px 0;
            margin: 8px 0 16px;
            font-size: 1rem;
        }

        input[type=submit] {
            background: white;
            border: 1px solid gray;
            color: black;
            padding: 8px 16px;
            outline: none;
            transition: 0.2s ease-out;
            font-weight: 800;

            &:hover {
                background: #35495e;
                color: #55eca9;
                border-color: #35495e;
                cursor: pointer;
            }
        }
    }
</style>