<script>
  import Todo from "./components/Todo.svelte";

  let todos = [];
  let newTodoText = "";

  const addTodo = () => {
    todos = [
      ...todos,
      { id: Date.now().toString(36), text: newTodoText, done: false },
    ];
    newTodoText = "";
  };

  const handleDone = (id) => {
    const result = todos.map((todo) => {
      if (todo.id === id) {
        todo.done = !todo.done;
      }
      return todo;
    });
    todos = result;
  };

  const deleteTodo = (id) => {
    const result = todos.filter((todo) => todo.id !== id);
    todos = result;
  };
</script>

<div class="main">
  <h1>SvelteのTODOアプリ</h1>
  <div class="todos">
    {#each todos as todo (todo.id)}
      <Todo {handleDone} {deleteTodo} {todo} />
    {/each}
  </div>
  <input type="text" bind:value={newTodoText} />
  <button on:click={addTodo} disabled={newTodoText === ""}>追加</button>
</div>

<style>
  .main {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .todos {
    width: 100%;
    margin: 0 auto;
  }
</style>
