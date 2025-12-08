<script>
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>
  
	<nav><a href ="/login">Login</a></nav>
  <nav><a href ="/register">Register</a></nav>
  <nav><a href ="/photoapp">Photoapp</a></nav>
  <nav><a href ="/shoppinglist">Shopping list</a></nav>
  <nav><a href ="/memory">Memory</a></nav>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

{@render children?.()}

<style>

:global(body), 
:global(html){
  margin: 0%;
  padding: 0%;
  height: 100vh;
  width: 100vw;
  justify-items: center;


}    

</style>
