<script lang="ts">
	import EditorScene from "$lib/components/editor/EditorScene.svelte";
	import { Canvas } from "@threlte/core";

</script>

<div style="touch-action: none; width: 100%; height: 100%;">
    <Canvas>
        <EditorScene />
    </Canvas>
</div>