<script lang="ts">
	import Scene from '$lib/test/Scene.svelte';
	import { T } from '@threlte/core';
	import { Canvas } from '@threlte/core';
	import { fly } from 'svelte/transition';

	export interface GridItemProps {
		title: string;
		model: any;
		group?: string;
        link?: string;
	}

	const { title, model, group, link }: GridItemProps = $props();

    let isHovered = $state(false);
</script>

<button 
    class="flex flex-wrap p-4 justify-start bg-neutral-700" 
    onclick={() => {}}
    onmouseenter={() => isHovered = true}
    onmouseleave={() => isHovered = false}
>
    <div class="w-full h-32 bg-neutral-800">
        <Canvas>
            <!-- temp picture -->
            <Scene x=5 y=5 tilt=0 />
        </Canvas>
    </div>

    <div class="w-full pt-4 flex justify-between items-baseline">
        {#if (isHovered)}
            <span in:fly={{ y: 10, duration: 250 }} class="text-2xl">Create</span>
        {:else}
            <span in:fly={{ y: -10, duration: 250 }} class="text-2xl">{title}</span>
        {/if}
        <span>{group}</span>
    </div>
</button>
