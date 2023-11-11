<script>
  import { createEventDispatcher } from 'svelte';
  
  const dispatch = createEventDispatcher();

  function addTask() {
    dispatch('taskAdded', {
      message: 'New task added!',
    });
  }
</script>

<button on:click={addTask}>Add Task</button>
