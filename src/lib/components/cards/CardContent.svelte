<script lang="ts">
	let { class: className = '', children } = $props();
</script>

<div class={`p-6 pt-0 ${className}`}>
	{@render children?.()}
</div>
