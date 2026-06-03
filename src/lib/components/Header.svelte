<script lang="ts">
	import '../../app.css';
	import '../constants/navigation.ts';
	import type { NavLink } from '../constants/navigation.ts';
	import { resolve } from '$app/paths';
	import { Switch } from 'bits-ui';
	import { Sun, Moon } from 'lucide-svelte';
	import { browser } from '$app/environment';
	import Page from '../../routes/+page.svelte';

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

	let isDarkMode = $state(false);
	let isTransitioning = $state(false);
	function toggleTheme(checked: boolean) {
		if (isTransitioning) return;

		if (!document.startViewTransition()) {
			isDarkMode = checked;
			document.documentElement.classList.toggle('dark', isDarkMode == true);
			return;
		}

		isTransitioning = true;

		let transition = document.startViewTransition(() => {
			isDarkMode = checked;
			document.documentElement.classList.toggle('dark', isDarkMode == true);
		});

		transition.finished.finally(() => {
			isTransitioning = false;
		});
	}

	$effect(() => {
		if (!browser) return;
		const savedTheme = localStorage.getItem('isDarkMode') as true | false | null;
		if (savedTheme) {
			isDarkMode = savedTheme;
		} else {
		localStorage.setItem('isDarkMode',isDarkMode.toString());
            document.documentElement.classList.toggle('dark', isDarkMode == true);
		}
	});
</script>

<div
	class="sticky top-0 z-50 border-b border-border bg-background/95 backdrop-blur supports-backdrop-filter:bg-background/60">
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
		<div class="flex items-center justify-between h-16 text-base">
			<div>Read Me</div>
			<div class="flex items-center justify-center gap-10">
				{#each headerLinks as link (link)}
					{#if !link.isDisabled}
						<a
							class="text-sm text-muted-foreground hover:text-foreground transition-colors"
							href={resolve(link.href)}>
							{link.name}
						</a>
					{/if}
				{/each}
			</div>
			<div class="flex justify-center items-center gap-5">
				<div class="flex items-center space-x-3">
					<Switch.Root
						checked={isDarkMode}
						onCheckedChange={toggleTheme}
						class="bg-toggle relative h-8 w-14 rounded-full p-0.5 items-center justify-between flex">
						<Sun
							size={14}
							class="pointer-events-none absolute left-2 z-10 text-toggle-foreground" />

						<Moon
							size={14}
							class="pointer-events-none absolute right-2 z-10 text-toggle-foreground" />
						<Switch.Thumb
							class="bg-background shadow-mini absolute left-0.5 top-1/2 flex size-7 -translate-y-1/2 items-center justify-center rounded-full transition-transform data-[state=checked]:translate-x-6">
						</Switch.Thumb>
					</Switch.Root>
				</div>
				<div>Login</div>
			</div>
		</div>
	</div>
</div>
