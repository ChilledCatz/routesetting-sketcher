<script lang="ts">
    import { T } from "@threlte/core";
	import type { GridItemProps } from "$lib/components/ThrelteGridItem.svelte";
	import ThrelteGridItem from "$lib/components/ThrelteGridItem.svelte";

    const props: GridItemProps = { 
        title: 'Test wall', 
        model: '',
        group: 'Local Bouldering Gym'
    }
</script>

<div class="grid grid-cols-4 gap-2">
    <ThrelteGridItem {...props} />
    <ThrelteGridItem {...props} />
    <ThrelteGridItem {...props} />
    <ThrelteGridItem {...props} />
</div>