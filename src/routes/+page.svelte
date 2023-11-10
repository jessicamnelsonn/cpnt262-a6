<script>

let newItem = '';

let todoList = [
  {
    text: 'Buy groceries', 
    status: true
  },
  {
    text: 'Complete coding assignment', 
    status: true
  },
  {
    text: 'Update resume and LinkedIn profile', 
    status: true
  },
  {
    text: 'Go for a 30 minute walk', 
    status: false
  },
  {
    text: 'Learn a new programming language feature', 
    status: false
  },
  {
    text: 'Try a new recipe for dinner', 
    status: false
  },
];

function addToList() {
  todoList = [...todoList, {text: newItem, status: false}];
  newItem = '';
}

function removeFromList(index) {
  todoList.splice(index, 1)
  todoList = todoList;
  }

</script>

<main>

{#each todoList as { text, status }, index}
  <div style={status ? 'text-decoration: line-through;' : ''}>
    {text}
    <button on:click={() => removeFromList(index)}>Remove</button>
  </div>
{/each}

<input bind:value={newItem} placeholder="Enter new task" />
<button on:click={addToList}>Add Task</button>

</main>




