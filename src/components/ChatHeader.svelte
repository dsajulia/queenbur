<script>
	let { title = 'Esse é um trabalho para as Giulias e Julias' } = $props();
</script>

<header class="chat-header">

	<h1>{title}</h1>
</header>

<style>
	.chat-header {
		padding: 1rem;
		border-bottom: 1px solid #e5e7eb;
	}

	h1 {
		margin: 0;
		font-size: 1.25rem;
	}
</style>
