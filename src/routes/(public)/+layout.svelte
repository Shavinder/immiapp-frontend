<script>
	let { children } = $props();
</script>
<main class="flex h-screen w-screen justify-center p-4 mt-20">
    <div>
        {@render children()}
    </div>
    
</main>
