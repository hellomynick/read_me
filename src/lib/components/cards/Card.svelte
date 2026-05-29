<script lang="ts">
	let { class: className = '', children } = $props();
</script>

<div class={`rounded-xl border bg-background shadow-sm ${className}`}>
	{@render children?.()}
</div>
