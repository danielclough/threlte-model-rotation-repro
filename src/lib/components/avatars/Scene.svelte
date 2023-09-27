<script>
	import { T } from "@threlte/core";
	import {
		ContactShadows,
		HTML,
		OrbitControls,
	} from "@threlte/extras";
	import { Suspense } from "@threlte/extras";
	import avatars from "./gltf/index";

	let actions = [
		"Death",
		"Defeat",
		"Idle",
		"Jump",
		"PickUp",
		"Punch",
		"RecieveHit",
		"Roll",
		"Run",
		"Run_Carry",
		"Shoot_OneHanded",
		"SitDown",
		"StandUp",
		"SwordSlash",
		"Victory",
		"Walk",
		"Walk_Carry",
	];
	$: prevAction = ""
	$: nextAction = "Idle";
	let distanceFactor = 5;
</script>

<T.PerspectiveCamera makeDefault up={[0, 0, 1]} position={[2, -3, 2]} fov={120}>
	<OrbitControls
		on:create={({ ref }) => {
			ref.update();
		}}
		target={[2, 5, 1]}
	/>
</T.PerspectiveCamera>

<HTML>
	<div class="row">
		{#each actions as act}
			<button style="padding:1rem" on:click={() => {
				prevAction = nextAction
				nextAction = act
			}}
				>{act}</button
			>
		{/each}
	</div>
</HTML>
{#each avatars as avatar, i}
	<Suspense>
		<svelte:component
			this={avatar.model}
			bind:nextAction
			bind:prevAction
			position={[distanceFactor * i, 0, 0]}
			rotation={[Math.PI / 2, 0, 0]}
		/>
	</Suspense>
{/each}

<T.DirectionalLight intensity={0.5} position.x={-500} position.y={-220} />
<T.DirectionalLight intensity={0.5} position.x={500} position.y={-220} />
<T.AmbientLight intensity={1} />

<ContactShadows scale={10} blur={2} far={2.5} opacity={0.5} />

<style>
	.row {
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
	}
</style>