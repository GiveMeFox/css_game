<script lang="ts">
	import '../app.css';
	import { DarkMode } from 'flowbite-svelte';
	let btnClass = 'text-gray-500 dark:text-gray-400 hover:bg-gray-100 dark:hover:bg-gray-700 rounded-lg text-xl p-2';

	let { children } = $props();
</script>

<span class="sticky top-0 flex justify-between items-center p-3">
	<span><h1>pierdol sie</h1></span>
	<DarkMode {btnClass} />
</span>
<span class="h-[100%]">
{@render children()}
</span>

