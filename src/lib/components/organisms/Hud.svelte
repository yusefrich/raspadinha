<script lang="ts">
    import { createEventDispatcher } from 'svelte';
	import ScratchGroup from '$lib/components/molecules/ScratchGroup.svelte';
	import InputGroup from '$lib/components/molecules/InputGroup.svelte';
	import PlayerInfo from '$lib/components/atoms/PlayerInfo.svelte';
    export let scratchs:any = [];
    export let count = 0;

    const dispatch = createEventDispatcher();

    function scratchSingleCard() {
        dispatch('scratchSingleCard');
        count++;
    }
    function scratchAll() {
        dispatch('scratchAll');
        count++;
    }
    function openStore() {
        dispatch('openStore');
    }
    function openInventory() {
        dispatch('openInventoy');
    }
</script>

<section>
	{#key count}
        <ScratchGroup scratchs={scratchs} />
	{/key}
    <InputGroup on:scratchSingleCard={scratchSingleCard} on:scratchAll={scratchAll} on:openStore={openStore} on:openInventoy={openInventory} />
    <PlayerInfo />
</section>

<style>
    section {
        width: 100vw;
        height: 100vh;
        position: absolute;
        top: 0;
        left: 0;
        overflow: hidden;
        /* border: solid 10px yellow; */
    }
</style>