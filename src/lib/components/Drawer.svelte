<script>
	import { Modal } from '@skeletonlabs/skeleton-svelte';

	let drawerState = $state(false);

	function drawerClose() {
		drawerState = false;
	}
	let {pages, pagesAdmin} = $props();
</script>

<!--
Tips for Drawer modals:
- Use `contentBase` to set styles, incuding height/width
- Set justify-start to align to the left
- Clear the align and padding styles
- Use `positionerClasses` to set the
- Set transition.x values that matches content width in pixels
-->

<Modal
	bind:open={drawerState}
	triggerBase=""
	contentBase="bg-surface-100-900 p-4 space-y-4 shadow-xl w-[480px] h-screen flex flex-col justify-between"
	positionerJustify="justify-start"
	positionerAlign=""
	positionerPadding=""
	transitionsPositionerIn={{ x: -480, duration: 200 }}
	transitionsPositionerOut={{ x: -480, duration: 200 }}
>
	{#snippet trigger()}
		<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-layout-sidebar" viewBox="0 0 16 16">
			<path d="M0 3a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v10a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2zm5-1v12h9a1 1 0 0 0 1-1V3a1 1 0 0 0-1-1zM4 2H2a1 1 0 0 0-1 1v10a1 1 0 0 0 1 1h2z"/>
	  	</svg>
	{/snippet}
	{#snippet content()}
		<header class="flex justify-end p-4">
			<button type="button" onclick={drawerClose} aria-label="Close Drawer">
				<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-x-lg" viewBox="0 0 16 16">
					<path d="M2.146 2.854a.5.5 0 1 1 .708-.708L8 7.293l5.146-5.147a.5.5 0 0 1 .708.708L8.707 8l5.147 5.146a.5.5 0 0 1-.708.708L8 8.707l-5.146 5.147a.5.5 0 0 1-.708-.708L7.293 8z"/>
				  </svg>
			</button>
		</header>
		<ul class="list-none space-y-4">
            {#each pages as page}
			<li>
				<a href={page.href} class="w-full px-3 py-2 rounded-2xl btn preset-tonal-secondary">
					{page.name}
				</a>
			</li>
            {/each}
        </ul>
		<footer>
			
		</footer>
	{/snippet}
</Modal>