<script lang="ts">
	import { T, Canvas } from "@threlte/core";
	import { Gizmo, Grid, OrbitControls, Outlines } from "@threlte/extras";
	import { CylinderGeometry, Group } from "three";
</script>

<Canvas>
    <T.PerspectiveCamera
        makeDefault
        position={10}
    >
        <OrbitControls>
            <Gizmo 

            />
        </OrbitControls>
    </T.PerspectiveCamera>

    <T.Group>
        <T.Mesh position={[ 0, 0, 0 ]}>
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

    <Grid position={[ 0, -5.001, 0 ]} />
</Canvas>