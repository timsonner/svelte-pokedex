<script>
  import "../app.css"
  import 'uno.css'
  import NavigationBar from "$lib/navigationBar.svelte";
</script>

<div class="p-8 max-w-6xl mx-auto">
  <NavigationBar />
<slot></slot>
</div>