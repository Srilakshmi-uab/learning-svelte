<script>
  import { afterUpdate } from 'svelte';

  afterUpdate(() => {
    document.querySelector('.js-todo-input').focus();
  });

  let todoItems = [];
  let newTodo = '';

  function addTodo() {
    newTodo = newTodo.trim();
    if (!newTodo) return;
    var options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };

    const todo = {
      text: newTodo,
      checked: false,
      date: new Date().toLocaleDateString("en-US", options),
      id: Date.now(),
    };

    todoItems = [...todoItems, todo];
    newTodo = '';
  }

  function toggleDone(id) {
    const index = todoItems.findIndex(item => item.id === Number(id));
    todoItems[index].checked = !todoItems[index].checked;
  }

  function deleteTodo(id) {
    todoItems = todoItems.filter(item => item.id !== Number(id));
  }
</script>
<header class="header"> <h1 class="app-title-header">Srilakshmi To Do List</h1></header>
<main>

<article>
  <div class="container">
   
    <ul class="todo-list">
      {#each todoItems as todo (todo.id)}
      <div on:click={() => toggleDone(todo.id)}>
            <label>Created-on: {todo.date}</label>
      
            <li class="todo-item {todo.checked ? 'done' : ''}">
            
            
              <input id={todo.id} type="checkbox" />
            
              <label for={todo.id} class="tick" ></label>
              <span>{todo.text}</span>
              <button class="delete-todo" on:click={() => deleteTodo(todo.id)}>
                <svg><use href="#delete-icon"></use></svg>
              </button>
            
            </li>
          </div>
      {/each}
    </ul>
    <div class="empty-state">
     
      <h2 class="empty-state__title">Add your first todo</h2>
      <p class="empty-state__description">What do you want to get done today?</p>
    </div>
    <form on:submit|preventDefault={addTodo}>
      <input class="js-todo-input" type="text" aria-label="Enter a new todo item" placeholder="E.g. have to go to Gym at 7pm" bind:value={newTodo}>
    </form>
  </div>
</article>
</main>

