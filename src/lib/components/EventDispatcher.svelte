<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  function addToList() {
    dispatch('taskAdded', {
      message: 'New task added!',
    });
  }
</script>

<button on:click={addToList} class="ml-4 px-6 py-2 bg-blue-500 text-white rounded-md">Add Task</button>
