<template>

  <div>
    <div>
      <AddTodo/>
    </div>
    <h3>Livros
    </h3>
    <div class="todos">
      <div
       
        v-for="todo in allTodos"
        :key="todo.id"
        :id="todo.id"
        class="todo"
        :class="{'is-complete':todo.completed}"
      >
      <router-link
           tag="h5"
           :to="{ name: 'detailTodo', params: { id: todo.id } }"
       >
        {{ todo.title }}
      </router-link>
      
        <div><p> {{ todo.description }}</p></div>
        <i @click="deleteTodo(todo.id)" class="fas fa-trash-alt"></i>
       
      </div>
    </div>
  </div>
</template>


<script>
import { mapGetters, mapActions } from "vuex";
import AddTodo from './AddTodo.vue'
export default {
  name: "todos",
  components:{AddTodo},
  methods: {
    ...mapActions(["getTodos", "deleteTodo"]),

  },
  computed: mapGetters(["allTodos"]),
  created() {
    this.getTodos();
  }
};
</script>

<style scoped>
.todos {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 1rem;
}
.todo {
  border: 1px solid #ccc;
  background: #00CED1;
  padding: 1rem;
  border-radius: 5px;
  text-align: center;
  position: relative;
  cursor: pointer;
}
i {
  position: absolute;
  bottom: 10px;
  right: 10px;
  cursor: pointer;
  color: #fff;
}
.legend {
  display: flex;
  justify-content: space-around;
  margin-bottom: 1rem;
}
.complete-box {
  display: inline-block;
  width: 10px;
  height: 10px;
  background: #35495e;
}
.incomplete-box {
  display: inline-block;
  width: 10px;
  height: 10px;
  background: #41b883;
}
.is-complete {
  background: #008B8B;
  color: #fff;
}
@media (max-width: 500px) {
  .todos {
    grid-template-columns: 1fr;
  }
}
</style>
