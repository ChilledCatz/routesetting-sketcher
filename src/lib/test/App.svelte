<script lang="ts">
    import { Pane, Slider } from 'svelte-tweakpane-ui'
    import { Canvas } from '@threlte/core';
    import Scene from './Scene.svelte';
	import { Stars } from '@threlte/extras';

    let x = $state(5);
    let y = $state(5);
    let tilt = $state(0);
</script>

<Pane
    title="size"
    position="fixed"
>
    <Slider
        bind:value={x}
        min={1}
        max={10}
        format={(v) => v.toFixed(2)}
        label='width'
    />
    <Slider
        bind:value={y}
        min={1}
        max={10}
        format={(v) => v.toFixed(2)}
        label='height'
    />
    <Slider
        bind:value={tilt}
        min={-1}
        max={1}
        format={(v) => v.toFixed(2)}
        label='tilt'
    />
</Pane>

<div class="bg-slate-800">
    <Canvas>
        <Stars />
        <Scene x={x} y={y} tilt={tilt} />
    </Canvas>
</div>

<style>
    div {
        height: 100%;
    }
</style>