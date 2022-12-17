<script>
  import { v4 as uuidv4 } from "uuid";

  let inputVal = "";
  let todos = [];

  function addTodo() {
    if (inputVal && !todos.includes(inputVal)) {
      todos = [...todos, { id: uuidv4(), title: inputVal, isCompleted: false }];
      inputVal = "";
    }
  }

  function handleToggle(index) {
    const todo = todos[index];
    todos[index].isCompleted = !todo.isCompleted;
    todos = todos;
    console.log(todos);
  }

  function removeTodo(id) {
    todos = todos.filter(todo => todo.id !== id);
  }
</script>

<h2>
	Todo List
</h2>
<input type="text" placeholder="Add todo" bind:value={inputVal}>
<button on:click={addTodo}>Add todo</button>
<br><br>
{#each todos as todo, index (todo.id)}
  <input type="checkbox" name={todo.title} checked={todo.isCompleted} on:change={() => handleToggle(index)}>
  <label 
    for={todo.title} 
    style:color={todo.isCompleted ? 'gray' : ''}
    style:text-decoration={todo.isCompleted ? 'line-through' : ''}
  >
    {todo.title}
  </label>
  <button on:click={() => removeTodo(todo.id)} style="text-transform: line-through">Remove</button>
  <br><br>
{/each}

<style>
  .striked {
    text-decoration: line-through;
    color: gray;
  }
</style>