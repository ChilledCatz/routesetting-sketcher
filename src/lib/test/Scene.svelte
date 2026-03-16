<script>
	import { T } from '@threlte/core';
	import { OrbitControls } from '@threlte/extras';

    let { x, y, tilt } = $props();
</script>

<T.PerspectiveCamera 
    makeDefault
    position={[5, 5, 5]}
    oncreate={(ref) => {
        ref.lookAt(0, 0, 0);
    }}
/>

<T.Mesh rotation={[tilt, 0, 0]}>
	<T.PlaneGeometry args={[x, y]} />
	<T.MeshBasicMaterial color="blue" />
</T.Mesh>
