<script>
	import '$lib/style/colors.css';
	import '$lib/style/vars.css';
	import '$lib/style/main.css';

    import Navbar from "$lib/components/navbar/navbar.svelte"
	import BackToTop from '$lib/back-to-top.svelte';
</script>

<svelte:head>
	<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
	<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/devicon.min.css">
</svelte:head>

<Navbar />
<BackToTop />
<slot />