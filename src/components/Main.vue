<template>
    <div class="main">
        <ul>
            <!-- <li v-for="todo in todos" :key="todo.time" :style="{color:color}"> -->
 
            <li v-for="todo in todos" :key="todo.time" :class="{red: !todo.completed, green: todo.completed}">
                               {{todo.text}}
             <!-- <div v-show="todo.completed === false">{{todo.text | capitalize}}</div> -->
             <!-- <img :src= "'html'+srcUrl">{{todo.text}} -->
            </li>
                <p>
                {{message}}
            </p>
            <input type="text" v-model="message">
            <button @click="save()">Save</button>
            </ul> 
    </div>
</template>

<script>
export default {
    watch:
    {
        todos(oldVal,newVal)
        {
            console.log(oldVal,newVal)
        }
    },
    beforeCreate()
    {
        console.log("before create")
    },
    mounted() 
    {
        console.log("mounted")
    },
    updated()
    {},
    computed: {
        sortItem()
        {
            return this.todos.sort((a,b)=>{b.time-a.time})
        }
    },
    methods: {
        save2() {
            this.save() 
        },
            save() 
            {
                console.log('save')
            }
    },
    name: 'Main',
    filters: {
        capitalize(val)
        {
            return val.toUpperCase()
        }
    },
    data(){
        return {
            message: "test", 
            color: 'red',
            srcUrl: 'https://via.placeholder.com/20',
            todos: [
                {text: 'Todo1',
                 time: 154035257,
                 completed: true},
                 {text: 'Todo2',
                 time: 154035229,
                 completed: true},
                 {text: 'Todo3',
                 time: 154035258,
                 completed: false},
                 {text: 'Todo4',
                 time: 154035260,
                 completed: false},
                 {text: 'Todo5',
                 time: 154035266,
                 completed: true},

                

            ]
        }
    }       
}
</script>
<style scoped>
.red{
    color: crimson 
}
.green{
    color: green
}
</style>
