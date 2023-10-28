<script>
// @ts-nocheck

    export let addTodo;
    export let toggleCompleted;
    export let todosAmount;

    let todo;

    function submitTodo() {
        addTodo(todo);
        todo = '';
    }
</script>

<form on:submit|preventDefault={submitTodo}>
    {#if todosAmount > 0}
    <input type="checkbox" id="toggle-all" class="toggle-all" on:click={toggleCompleted}>
    <label for="toggle-all" aria-label="Mark all as complete">
        Mark all as complete
    </label>
    {/if}
    <!-- svelte-ignore a11y-autofocus -->
    <input 
    bind:value={todo} 
    id="new-todo"
    class="new-todo"
    placeholder="What's the task for today?"
    autofocus
    >
</form>


<style>
    .toggle-all {
      width: 1px;
      height: 1px;
      position: absolute;
      opacity: 0;
    }
  
    .toggle-all + label {
      position: absolute;
      font-size: 0;
    }
  
    .toggle-all + label:before {
      content: '❯';
      display: block;
      padding: var(--spacing-16);
      font-size: var(--font-24);
      color: var(--color-gray-58);
      transform: rotate(90deg);
    }
  
    .toggle-all:checked + label:before {
      color: var(--color-gray-28);
    }
  
    .new-todo {
      width: 100%;
      padding: var(--spacing-16);
      padding-left: 60px;
      font-size: var(--font-24);
      border: none;
      border-bottom: 1px solid var(--shadow-1);
    }
</style>  