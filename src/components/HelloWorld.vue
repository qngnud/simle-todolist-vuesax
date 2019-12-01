<template>
    <div class="hello">
        <h1>{{ msg }}</h1>

        <h1 class="danger">To Do List</h1>
        <v-card class="mx-auto" max-width="300" tile>

        <v-container class="main vs-sm-4">
            <v-row>
                <v-col cols="12" sm="6" md="1">
                    <ul>
                        <li :key="todo.content" v-for="todo in todos">
                            <label>
                                <input type="checkbox" @change="check" v-model="todo.checked"/>
                            </label>
                            <span v-if="todo.checked" class="success">  {{todo.content}}</span>
                            <span v-if="!todo.checked" class="primary">  {{todo.content}}</span>
                        </li>
                    </ul>
                    <label>
                        <input @keyup.enter="add" v-model="newTodo" placeholder="Add new todo"/>
                    </label>
                </v-col>
            </v-row>
        </v-container>
        </v-card>

    </div>
</template>

<script>
    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        },
        data() {
            return {
                newTodo: '',
                todos: [
                    {
                        content: 'Buy a coffee',
                        checked: false
                    },
                    {
                        content: 'Take a shower',
                        checked: false
                    },
                    {
                        content: 'Thinking about life',
                        checked: false
                    },
                ]
            }
        },
        methods: {
            add: function () {
                let _newTodo = this.newTodo
                this.todos.push({content: _newTodo, checked: false})
            },
            check: function () {
                this.todos.checked = !this.todos.checked;
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style: square;
        padding: 0;
    }

    li {
        display: inline-block;
        align-content: start;
    }

    a {
        color: #42b983;
    }
</style>
