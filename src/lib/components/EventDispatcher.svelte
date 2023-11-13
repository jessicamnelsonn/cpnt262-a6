<script>
  // Importing Svelte functionality
  import { createEventDispatcher } from 'svelte';
  
  // Creating an event dispatcher
  const dispatch = createEventDispatcher();

  // Function to dispatch the 'taskAdded' event
  function addToList() {
    dispatch('taskAdded', {
      message: 'New task added!',
    });
  }
</script>
<!-- Button triggering the 'addToList' function with Tailwind CSS styles -->
<button on:click={addToList} class="px-6 py-2 bg-blue-500 text-white rounded-md">Add Task</button>
