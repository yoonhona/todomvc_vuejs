<template>
    <section class="todoapp">
        <header class="header">
            <h1>todos</h1>
            <input class="new-todo"
                   autofocus autocomplete="off"
                   placeholder="What needs to be done?"
            />
        </header>
        <section class="main">
            <input id="toggle-all" class="toggle-all" type="checkbox">
            <label for="toggle-all"></label>
            <ul class="todo-list">
                <li class="todo">
                    <div class="view">
                        <input class="toggle" type="checkbox">
                        <label></label>
                        <button class="destroy"></button>
                    </div>
                    <input class="edit" type="text">
                </li>
            </ul>
        </section>
        <footer class="footer">
        footer
        </footer>
    </section>
</template>

<script>
export default {
  name: 'app',
};

const STORAGE_KEY = 'todos-vuejs-2.0';
const todoStorage = {
  fetch() {
    var todos = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]');
    todos.forEach(function(todo, index) {
      todo.id = index;
    });
    todoStorage.uid = todos.length;
    return todos;
  },
  save(todos) {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(todos));
  },
};

const filters = {
  all(todos) {
    return todos;
  },
  active(todos) {
    return todos.filter(function(todo) {
      return !todo.completed;
    });
  },
  completed(todos) {
    return todos.filter(function(todo) {
      return todo.completed;
    });
  },
};
</script>

<style src="todomvc-app-css/index.css"></style>
