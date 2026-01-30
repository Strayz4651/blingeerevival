<script>
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
  import { base } from '$app/paths';
</script>
  
	<nav><a href ="{base}/login">Login</a></nav>
  <nav><a href ="{base}/register">Register</a></nav>
  <nav><a href ="{base}/photoapp">Photoapp</a></nav>
  <nav><a href ="{base}/shoppinglist">Shopping list</a></nav>
  <nav><a href ="{base}/memory">Memory</a></nav>
  <nav><a href ="{base}/chat">Chat</a></nav>


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
