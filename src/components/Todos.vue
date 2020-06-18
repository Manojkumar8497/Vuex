<template>
  <div id="todos">
    <h2>Todos</h2>
    <div class="legend">
      <span>Double click to mark as complete</span>
      <span>
        <span class="incomplete-box"></span> = Incomplete
      </span>
      <span>
        <span class="complete-box"></span> = Complete
      </span>
    </div>
    <div class="todos">
      <div class="todo" v-bind:class="{'is-complete':todo.completed}" @dblclick="onDblClick(todo)" v-for="todo in allTodos" :key="todo.id">
        {{todo.title}}
        <i class="fas fa-trash-alt" @click="deleteTodo(todo.id)"></i>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  name: "Todos",
  methods: {
    ...mapActions(["fetchTodos", "deleteTodo", "updateTodos"]),
    onDblClick(todo) {
      const upTodos = {
        id: todo.id,
        title: todo.title,
        completed: !todo.completed
      };
      this.updateTodos(upTodos);
    }
  },
  computed: mapGetters(["allTodos"]),
  created() {
    this.fetchTodos();
  }
};
</script>

<style scoped>
.todos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;
}

.todo {
  border: 1px solid #ccc;
  padding: 1rem;
  border-radius: 5px;
  position: relative;
  text-align: center;
  cursor: pointer;
  background: #41b883;
}

i {
  position: absolute;
  bottom: 10px;
  right: 10px;
  color: #fff;
  cursor: pointer;
}

.legend {
  display: flex;
  justify-content: space-around;
  margin-bottom: 1rem;
}

.complete-box {
  width: 10px;
  height: 10px;
  display: inline-block;
  background: #35495e;
}

.incomplete-box {
  width: 10px;
  height: 10px;
  display: inline-block;
  background: #41b883;
}

.is-complete{
  background: #35495e;
  color: #fff;
}

@media (max-width: 500px) {
  .todos {
    grid-template-columns: 1fr;
  }
}
</style>
