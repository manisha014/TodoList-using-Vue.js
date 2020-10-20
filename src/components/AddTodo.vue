<template>
    <div class="add-todo-wrap">
        <form @submit="addTodo">
            <input type="text" v-model="newTodo" name="newTodo" placeholder="Add Todo here...">
            <input type="submit" value="Add" class="addBtn btn">
        </form>
    </div>
</template>

<script>
export default {
    name: "AddTodo",
    data() {
        return {
            newTodo: ""
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();

            if(this.newTodo!=="") {
                const newTodoObj = {
                    title: this.newTodo,
                    completed: false
                }

                this.$emit('add-todo', newTodoObj);

                this.newTodo = "";
            }
        }
    }
}
</script>

<style scoped>
  form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  .addBtn {
    flex: 2;
  }
</style>