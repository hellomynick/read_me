<script lang="ts">
	let { class: className = '', children } = $props();
</script>

<h3 class={`font-semibold leading-none tracking-tight ${className}`}>
	{@render children?.()}
</h3>
