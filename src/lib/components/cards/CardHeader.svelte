<script lang="ts">
	let { class: className = '', children } = $props();
</script>

<div class={`flex flex-col space-y-1.5 p-6 ${className}`}>
	{@render children?.()}
</div>
