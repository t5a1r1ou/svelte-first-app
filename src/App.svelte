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

<div class="flex flex-col items-center w-screen h-screen bg-blue-500">
  <h1 class="text-3xl m-3">SvelteのTODOアプリ</h1>
  <div class="w-9/12 my-0 mx-auto">
    {#each todos as todo (todo.id)}
      <Todo {handleDone} {deleteTodo} {todo} />
    {/each}
  </div>
  <input
    type="text"
    bind:value={newTodoText}
    placeholder="TODOを入力してください"
    class="border border-gray-500 p-3 w-8/12"
  />
  <button
    on:click={addTodo}
    disabled={newTodoText === ""}
    class="bg-white my-4 mx-auto p-4 rounded">追加</button
  >
</div>
