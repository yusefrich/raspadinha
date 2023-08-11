<script lang="ts">
	import ScratchCard from '$lib/components/atoms/ScratchCard.svelte';
    export let scratchs:any = [];
</script>

<section>
    {#each scratchs as row}
        <div class="row">
            {#each row.cards as item}
                <ScratchCard scratched={item.scratched}/>
            {/each}
        </div>
    {/each}
</section>

<style lang="scss">
    @import "$lib/boilerplate/breakpoints";
    section {
        position: absolute;
        top: 45vh;
        left: 50vw;
        z-index: 1000;
        transform: translate(-50%, -50%);
        @include _md {
            top: 50vh;
            transform: translate(-50%, -60%);
        }
        /* border: solid 10px yellow; */
    }
    .row {
        display: flex;
    }
</style>