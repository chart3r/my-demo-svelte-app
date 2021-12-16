<script>
  import Header from '$lib/header/Header.svelte';
</script>

<Header />

<main>
  <slot />
</main>

<style>
@tailwind base;
@tailwind components;
@tailwind utilities;
</style>