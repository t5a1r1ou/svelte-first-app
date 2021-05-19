<script>
  export let todo;
  export let handleDone;
  export let deleteTodo;
</script>

<div
  class="flex items-center justify-between w-8/12 px-2 py-8 mx-auto my-4 rounded-md bg-white"
>
  <p class={todo.done ? "line-through m-1" : "m-1"}>{todo.text}</p>
  <div>
    <button
      class="m-1 p-3 rounded border border-gray-500"
      on:click={handleDone(todo.id)}>{todo.done ? "解除" : "完了"}</button
    >
    <button class="m-1 p-3 rounded bg-red-500" on:click={deleteTodo(todo.id)}
      >削除</button
    >
  </div>
</div>
