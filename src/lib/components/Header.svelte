<script lang="ts">
	import '../../app.css';
	import '../constants/navigation.ts';
	import type { NavLink } from '../constants/navigation.ts';
	import { resolve } from '$app/paths';
	import { ToggleGroup } from 'bits-ui';
	import { Sun, Moon } from 'lucide-svelte';

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

	let themes: string[] = $state(['light']);
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
							href={resolve(link.href)}
						>
							{link.name}
						</a>
					{/if}
				{/each}
			</div>
			<div class="flex justify-center items-center gap-5">
				<ToggleGroup.Root
					bind:themes
					type="single"
					class="h-input rounded-card-sm border-border bg-background-alt shadow-mini flex items-center gap-x-0.5 border px-[4px] py-1"
				>
					<ToggleGroup.Item
						aria-label="toggle bold"
						value="light"
						class="rounded-9px bg-background-alt hover:bg-muted active:bg-dark-10 data-[state=on]:bg-muted data-[state=off]:text-foreground-alt data-[state=on]:text-foreground active:data-[state=on]:bg-dark-10 inline-flex size-10 items-center justify-center transition-all active:scale-[0.98]"
					>
						<Sun />
					</ToggleGroup.Item>
					<ToggleGroup.Item
						aria-label="toggle bold"
						value="light"
						class="rounded-9px bg-background-alt hover:bg-muted active:bg-dark-10 data-[state=on]:bg-muted data-[state=off]:text-foreground-alt data-[state=on]:text-foreground active:data-[state=on]:bg-dark-10 inline-flex size-10 items-center justify-center transition-all active:scale-[0.98]"
					>
						<Moon />
					</ToggleGroup.Item>
				</ToggleGroup.Root>
				<div>Login</div>
			</div>
		</div>
	</div>
</div>
