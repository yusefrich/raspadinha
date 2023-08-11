<script>
    import { createEventDispatcher } from 'svelte';
	import PlayButton from '$lib/components/atoms/PlayButton.svelte';
	import AutoButton from '$lib/components/atoms/AutoButton.svelte';
	import NavButton from '$lib/components/atoms/NavButton.svelte';
    import inventory from '$lib/images/inventory.png';
    import store from '$lib/images/store.png';

    const dispatch = createEventDispatcher();

    function scratchSingleCard() {
        dispatch('scratchSingleCard');
    }
    function scratchAll() {
        dispatch('scratchAll');
    }
    function openStore() {
        dispatch('openStore');
    }
    function openInventory() {
        dispatch('openInventoy');
    }
</script>

<section>
    <div class="play-position">
        <PlayButton on:scratch={scratchSingleCard} />
    </div>
    <div class="auto-position">
        <AutoButton on:scratchAll={scratchAll} />
    </div>
    <div class="navbar-position">
        <NavButton image={inventory} on:cclick={openInventory} />
        <!-- <NavButton image={store} /> -->
        <NavButton image={store} on:cclick={openStore} />
    </div>
</section>

<style lang="scss">
    @import "$lib/boilerplate/breakpoints";
    section {
        position: absolute;
        right: -2vw;
        right: 0;
        bottom: 0;
        @include md {
            bottom: -6vh;
            z-index: 2000;
        }
        @include _md {
            width: 100vw;
        }
        // overflow: hidden;
        // transform: translate(-50%, -50%);
    }
    .play-position{
        @include _md {
            left: 10vw;
            position: relative;
        }
    }
    .navbar-position{
        position: absolute;
        bottom: 1vh;
        right: 2vw;
        @include md {
            right: 8vw;
            bottom: 50vh;
        }
    }
    .auto-position{
        position: absolute;
        // left: 0;
        bottom: 10px;
        @include md {
            right: 17vw;
        }
        @include _md {
            left: 5vw;
        }
    }
</style>