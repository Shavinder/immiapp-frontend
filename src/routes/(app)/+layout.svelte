<script>
	let { children } = $props();
    import UserMenu from '$lib/components/UserMenu.svelte';
    import Drawer from '$lib/components/Drawer.svelte';
    import Lightswitch from '$lib/components/Lightswitch.svelte';

    const pages = [
        {name: "Dashboard", href: "/dashboard"},
        {name: "Cases", href: "/cases"},
        {name: "Clients", href: "/clients"},
    ];
    const pagesAdmin = [
        {name: "Invoices", href: "/users"},
        {name: "Payments", href: "/payments"},
    ];

</script>

<div class="flex flex-col min-h-screen">
    <div class="header border-b flex justify-between items-center p-4 ">
        <div class="md:hidden">
            <Drawer {pages} {pagesAdmin}/>
        </div>
        <div> <a href="/" class="font-bold">My App</a></div>
        
        <nav class="space-x-4 hidden md:flex">
            {#each pages as page}
            <a href={page.href} class="px-3 py-2 rounded-2xl hover:bg-gray-200">
                {page.name}
            </a>
            {/each}
        </nav>
        <div class="flex items-center space-x-4">
            <Lightswitch />
            <UserMenu />
        </div>
        
    </div>
    <main class="flex-1 p-4">
        {@render children()}
    </main>
    <footer class="bg-gray-800 text-white py-4 px-8">
      <p>&copy; 2023 My Website</p>
    </footer>
  </div>
