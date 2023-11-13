<script>
import EventDispatcher from '../lib/components/EventDispatcher.svelte'

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
    if (newItem) {
      todoList = [...todoList, { text: newItem, status: false }];
      newItem = ''; 
    }
  }

function removeFromList(index) {
  todoList.splice(index, 1)
  todoList = todoList;
}

function handleTaskAdded(event) {
  alert(event.detail.message);
  if (newItem) {
    todoList = [...todoList, { text: newItem, status: false }];
    newItem = '';
  }
}

</script>

<main class="max-w-md mx-auto mt-8 p-4 bg-gray-100 shadow-md rounded-md">

  <h1 class="text-center text-4xl p-2">To-Do List</h1>

  {#each todoList as { text, status }, index}
    <div class="flex items-center justify-between bg-white rounded-md p-4 mb-4 shadow-md">
      <span class="{status ? 'line-through text-gray-500' : 'text-black'}">{text}</span>
      <button class="ml-2 px-4 py-2 bg-red-500 text-white rounded-md" on:click={() => removeFromList(index)}>Remove</button>
    </div>
  {/each}

  <section class="flex items-center mb-4">
    <input class="flex-1 p-2 border border-gray-300 rounded-md" bind:value={newItem} placeholder="Enter new task" />
    <EventDispatcher on:taskAdded={handleTaskAdded}>
      <button on:click={addToList}>Add Task</button>
    </EventDispatcher>
  </section>
  
  </main>




