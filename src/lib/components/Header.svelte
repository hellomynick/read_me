<script lang="ts">
	import '../../app.css';
	import '../constants/navigation.ts';
	import type { NavLink } from '../constants/navigation.ts';

	const headerLinks: NavLink[] = [
		{
			name: 'Home',
			href: '/',
			isDisabled: false
		},
		{
			name: 'Manga',
			href: '/manga',
			isDisabled: false
		}
	];
</script>

<div
	class="sticky top-0 z-50 border-b border-border bg-background/95 backdrop-blur supports-backdrop-filter:bg-background/60"
>
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
		<div class="flex items-center justify-between h-16 text-base">
			<div>Read Me</div>
			<div class="flex items-center justify-center gap-10">
				{#each headerLinks as link (link)}
					{#if !link.isDisabled}
						<a
							class="text-sm text-muted-foreground hover:text-foreground transition-colors"
							href={link.href}>{link.name}</a
						>
					{/if}
				{/each}
			</div>
			<div>Login</div>
		</div>
	</div>
</div>
