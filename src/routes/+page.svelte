<script>
// Importing components
import EventDispatcher from '../lib/components/EventDispatcher.svelte'
import ExtraComponent from '../lib/components/ExtraComponent.svelte';

// State variables
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


// Function to remove an item from the todoList
function removeFromList(index) {
  // Remove the item at the specified index
  todoList.splice(index, 1)
  // Update the todoList state
  todoList = todoList;
}

// Function to handle the addition of a new task
function handleTaskAdded(event) {
  // Display an alert with a message from the event
  alert(event.detail.message);
  // Check if newItem is not empty before adding it to the todoList
  if (newItem) {
    // Add the new task to the todoList
    todoList = [
      ...todoList, 
    { 
      text: newItem, 
      status: false 
    }
  ];
    // Reset newItem after adding it to the list
    newItem = '';
  }
}

// State variable for button color
let buttonColor = 'red';

// Function to change the button color
function changeButtonColor() {
  // Toggle between red and blue
  buttonColor = buttonColor === 'red' ? 'purple' : 'red';
}

</script>
<!-- Main content area with Tailwind CSS styles -->
<main class="max-w-md mx-auto mt-8 p-4 bg-gray-100 shadow-md rounded-md">

  <!-- Title for the To-Do List -->
  <h1 class="text-center text-4xl p-2">To-Do List</h1>

  <!-- Loop through each item in the todoList -->
  {#each todoList as { text, status }, index}
    <section class="flex items-center justify-between bg-white rounded-md p-4 mb-4 shadow-md">
      <!-- Display task text with strikethrough if completed -->
      <span class="{status ? 'line-through text-gray-500' : 'text-black'}">{text}</span>
      <!-- Button to remove the task -->
      <button class="ml-2 px-4 py-2 text-white rounded-md" on:click={() => { removeFromList(index); changeButtonColor(); }} style="background-color: {buttonColor}">Remove</button>
    </section>
  {/each}

  <!-- Input section to add a new task -->
  <section class="flex items-center mb-4">
    <input class="flex-1 p-2 border border-gray-300 rounded-md" bind:value={newItem} placeholder="Enter new task" />
    <!-- Using ExtraComponent to wrap EventDispatcher with a title -->
    <ExtraComponent title="Task Tracker">
      <EventDispatcher on:taskAdded={handleTaskAdded}></EventDispatcher>
    </ExtraComponent>
  </section>

  </main>




