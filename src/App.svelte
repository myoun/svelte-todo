<script lang="ts">
import { writable } from 'svelte/store';

	import { storeFE, idIncrement } from './store.js';
	import TodoElement from "./TodoElement.svelte";
	$storeFE = [
	]
	function getCookie(): Array<string> {
		const semi = document.cookie.split(";")
		const oc = semi[semi.length-1]
		let cookie =  `",${oc},"`.split('","').filter((value:string) => value.trim() != "")
		console.log(cookie)
		return cookie
	}

	getCookie().forEach((value, idx) => {
		console.log(value)
		$storeFE[idx] = value
	})
	
	
	export function enter(e: KeyboardEvent) {
		if (e.key === "Enter") {
			let content = (document.getElementById("content") as HTMLInputElement)
			let value=  content.value
			let l = $storeFE.length
			if (value.trim() == "") return
			content.value = ""
			$storeFE[l] = { value : value}
			let cookiestr = ""
			$storeFE.forEach((value:string) => {
				cookiestr += `"${value.value}",`
			})
			cookiestr = cookiestr.slice(0,cookiestr.length-1)
			document.cookie = cookiestr;
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