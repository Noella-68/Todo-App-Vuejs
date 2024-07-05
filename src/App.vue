<template>
  <div>
    <header>
        <div>
          <nav class="navbar">
          <img src="/images/Logo.jpeg"  class="logo">
        </nav>
        </div>
    </header>
  </div>
  <TodoList> </TodoList>
</template>

<script>
import TodoList from './components/TodoList.vue';

export default {
  name: 'App',
  components: {
    TodoList
  }
}
</script>

<style>
header {
  background-color: rgb(48, 47, 47);
  color: white;
  padding: 10px 0;
}

.navbar {
  display: flex;
  justify-content: center;
}

.logo {
  height: 45px;

}
</style>
