<script lang="ts">
	import { onMount } from 'svelte';
	import Goal from '$lib/components/organisms/Goal.svelte';
	import Hud from '$lib/components/organisms/Hud.svelte';
	import Publicity from '$lib/components/organisms/Publicity.svelte';
	import Stadium from '$lib/components/organisms/Stadium.svelte';
	import Victory from '$lib/components/atoms/Victory.svelte';
	import Store from '$lib/components/organisms/Store.svelte';
	import Inventory from '$lib/components/organisms/Inventory.svelte';
    import win from "$lib/sounds/success.mp3";
    import soundtrack from "$lib/sounds/soundtrack.mp3";

    let audio: HTMLAudioElement;
    let audio2: HTMLAudioElement;
	let loop = true;
	onMount(async () => {
		setTimeout(() => {
			audio2.play()
		},1000)	
	});
	let gameManager = {
		sound: true,
		scratched: [
			{
				row: 1,
				cards: [
					{ prize: true, scratched: true },
					{ prize: true, scratched: false },
					{ prize: true, scratched: false },
					{ prize: true, scratched: false }
				]
			},
			{
				row: 1,
				cards: [
					{ prize: true, scratched: false },
					{ prize: true, scratched: false },
					{ prize: true, scratched: false },
					{ prize: true, scratched: false }
				]
			}
		]
	}
	let storeModal = false
	let inventoryModal = false
	let victoryModal = false
	function checkWin () {
		let winCount = 0
		gameManager.scratched.forEach(groups => {
			groups.cards.forEach(card => {
				if (card.scratched && card.prize) {
					winCount++
				}
			})
		})
		if (winCount >= 3) {
			victoryModal = true
			audio.play();
			if (audio.paused) {
				audio.play();
			}else{
				audio.currentTime = 0
			}
		}
	}
    function scratchSingleCard() {
		let active = false
		gameManager.scratched.forEach(groups => {
			groups.cards.forEach(card => {
				if (!card.scratched && !active) {
					card.scratched = true
					active = true
					return
				}
			})
		})
		checkWin()
    }
    function scratchAll() {
		gameManager.scratched.forEach(groups => {
			groups.cards.forEach(card => {
				if (!card.scratched) {
					card.scratched = true
					return
				}
			})
		})
		checkWin()
    }

</script>

<svelte:head>
	<title>Raspadinha!</title>
	<meta name="description" content="Raspadinha" />
</svelte:head>
<div class="container">
	<section>
		<Stadium />
		<Publicity />
		<Goal />
		<Hud scratchs={gameManager.scratched} on:scratchSingleCard={scratchSingleCard} on:scratchAll={scratchAll} on:openStore={()=>{storeModal = true}} on:openInventoy={()=>{inventoryModal = true}} />
		<Victory modalOpen={victoryModal} />
		<Store open={storeModal} on:close={()=>{storeModal = false}} />
		<Inventory open={inventoryModal} on:close={()=>{inventoryModal = false}} />
		<audio src={win} bind:this={audio}></audio>
		<audio loop={loop} src={soundtrack} bind:this={audio2}></audio>
	</section>
</div>
<style>
	.container {
		overflow: hidden;
		height: 100%;
	}
	section {
		height: 100vh;
		/* height: 100%; */
		/* max-height: 100vh; */
		width: 100vw;
		max-width: 100vw;
		background-color: #1a360a;
		background-image: url("$lib/images/bg.png");
		/* display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6; */
		/* border: solid 10px blue; */
	}
</style>
