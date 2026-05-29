<script lang="ts">
	import Card from '$lib/components/cards/Card.svelte';
	import CardContent from '$lib/components/cards/CardContent.svelte';
	import CardHeader from '$lib/components/cards/CardHeader.svelte';
	import CardTitle from '$lib/components/cards/CardTitle.svelte';
</script>

<div class="my-4 text-foreground font-bold text-lg">Welcome back, Vu</div>

<Card class="max-w-md">
	<CardHeader>
		<CardTitle>Manga</CardTitle>
	</CardHeader>

	<CardContent>
		<p>Welcome to my manga website.</p>
	</CardContent>
</Card>
