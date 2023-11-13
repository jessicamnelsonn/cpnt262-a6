<script>
  // Exporting a prop
  export let title;
</script>

<!-- Component with a title and slot for additional content, using Tailwind CSS styles -->
<section class="bg-gray-200 m-2 p-2 rounded-md">
  <h2 class="text-xl font-semibold mb-2">{title}</h2>
  <slot></slot>
</section>