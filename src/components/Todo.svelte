<script>
  export let todo;
  export let handleDone;
  export let deleteTodo;
</script>

<div class="todo">
  <p class={todo.done ? "done" : ""}>{todo.text}</p>
  <div>
    <button on:click={handleDone(todo.id)}>{todo.done ? "解除" : "完了"}</button
    >
    <button on:click={deleteTodo(todo.id)} class="delete">削除</button>
  </div>
</div>

<style>
  .todo {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 70%;
    padding: 0.4rem 2rem;
    margin: 1rem auto;
    border-radius: 15px;
    background-color: #ffffff;
  }
  .todo p,
  .todo button {
    margin: 5px 10px;
  }
  .done {
    text-decoration: line-through;
  }
  .delete {
    background-color: red;
  }
</style>
