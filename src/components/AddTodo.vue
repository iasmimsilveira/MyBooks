<template>

  <div>
    <img src="https://unibescultural.org.br/wp-content/uploads/elementor/thumbs/banner_cbl-ofy0fbs0068fhrj9tp76jt6mwa3q3modv5tpouj6kw.jpg">
    <h3>Adicionar Livro</h3>
    <div>
      <form @submit.prevent="onSubmit">
        <div><h2>Livro:</h2></div>
        <div><input type="text" v-model="todo_add.title" placeholder="Adicionar título"></div>
        <div><h2>Descrição:</h2></div>
        <div><input type="text" v-model="todo_add.description" placeholder="Adicionar gênero"></div>
        <div><input type="submit" value="Enviar"></div>
      </form>
      
    </div>
  </div>
</template>

<script>
import { mapActions } from "vuex";
export default {
  name: "AddTodo",
  data() {
    return {
      todo_add :{
        title: "",
        description: ""
      }
    };
  },
  methods: {
    ...mapActions(["addTodo"]),
    onSubmit() {
      this.addTodo(this.todo_add);
    }
  }
};
</script>

<style>
form {
  display: block;
}
input[type="text"],input[type="textarea"] {
  width: 100%;
  flex: 10;
  padding: 10px;
  border: 1px solid #1BBC9B;
  outline: 0;
}
input[type="submit"] {
  flex: 2;
  background: #66CDAA;
  border: 1px solid #1BBC9B;
  color: #fff;
  cursor: pointer;
  width: 100%;
  height: 40px;
  margin: 10px;
}
</style>
