<script>
	import goal from '$lib/images/goal2.png';
</script>

<div>
    <picture>
        <img src={goal} alt="Welcome" />
    </picture>
</div>

<style lang="scss">
    @import "$lib/boilerplate/breakpoints";
    div {
        position: absolute;
        top: 0;
        width: 100vw;
        height: 100vh;
        overflow: hidden;
    }
    img {
        object-fit: cover;
        @include _ct(800px) {
            object-fit: contain;
            // width: 135%;
            width: 141%;
            height: 115%;
            transform: translate(-14%, -7%);
        }
        width: 100%;
        height: 100%;
    }
</style>