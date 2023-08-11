<script>
    import defaultImage from '$lib/images/panel1.png';
    export let image = defaultImage;
</script>

<div>
    <picture>
        <img src={image} alt="banner 1" />
    </picture>
</div>

<style lang="scss">
    @import "$lib/boilerplate/breakpoints";
    img {
        width: 60vw;
        height: auto;
    }
</style>