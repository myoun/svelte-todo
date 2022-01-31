<script lang="ts">
	import { storeFE, idIncrement } from './store.js';
	import TodoElement from "./TodoElement.svelte";
	$storeFE = [
	]
	export function enter(e: KeyboardEvent) {
		if (e.key === "Enter") {
			let content = (document.getElementById("content") as HTMLInputElement)
			let value=  content.value
			if (value.trim() == "") return
			var l = $storeFE.length;
			content.value = ""
			$storeFE[l] = { value : value}
		}
	}

</script>

<style>
	main {
		text-align: center;
	}
	h1 {
		text-align: center;
		font-size: 10rem;
		margin-bottom: 0.5rem;
	}
	#input {
		text-align: center;
		margin-bottom: 1rem;
	}
	#content {
		font-size: 150%;
		text-align: center;
		width: 40%;
		height: 50px;
	}
</style>

<main>
	<h1>TODOS</h1>
	<div id="input">
		<input id="content" type="text" on:keyup="{enter}">
	</div>
	<div id="todos">
		{#each $storeFE as todo}
			<TodoElement value="{todo.value}"></TodoElement>
		{/each}
	</div>
</main>