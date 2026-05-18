<script lang="ts">
    import type { Intersection, Vector3 } from "three";
	import { T } from "@threlte/core";
	import { Gizmo, Grid, interactivity, OrbitControls, Outlines } from "@threlte/extras";
	import { CylinderGeometry } from "three";

    interactivity();

    interface Hold {
        x: number,
        y: number,
        z: number
    }

    let holds = $state<Hold[]>([]);
    
    function createHold(event: Intersection) {
        const point = event.point
        holds.push({ x: point.x, y: point.y, z: point.z });
    }
</script>

<T.PerspectiveCamera
        makeDefault
        position={10}
    >
        <OrbitControls>
            <Gizmo />
        </OrbitControls>
    </T.PerspectiveCamera>

    <T.Group>
        <T.Mesh 
            position={[ 0, 0, 0 ]}
            onclick={createHold}
        >
            <T.MeshBasicMaterial color="white"/>
            <T.CylinderGeometry args={[ 5, 7.5, 10, 8 ]} />

            <Outlines color="blue" thickness={0.2} />
        </T.Mesh>
        <T.LineSegments>
            <T.EdgesGeometry args={[new CylinderGeometry(5, 7.5, 10, 8)]} />
            <T.LineBasicMaterial 
                color="blue"
                lineWidth={2}
            />
        </T.LineSegments>
    </T.Group>

    <T.Group>
        {#each holds as hold}
            <T.Mesh
                position={[hold.x, hold.y, hold.z]}
            >
                <T.MeshBasicMaterial color="orange" />
                <T.SphereGeometry args={[ 1, 32, 16 ]} />
            </T.Mesh>
        {/each}
    </T.Group>

    <Grid position={[ 0, -5.001, 0 ]} />