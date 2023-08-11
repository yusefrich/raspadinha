<script>
	import Banner from '$lib/components/atoms/Banner.svelte';
    import image1 from '$lib/images/panel1.png';
    import image2 from '$lib/images/panel2.png';
    let dynamicImage1 = image1;
    let dynamicImage2 = image2;
</script>

<section>
    <div class="section-container">
        <div>
            <Banner image={dynamicImage1} />
        </div>
        <div>
            <Banner image={dynamicImage2} />
        </div>
        <div>
            <Banner image={dynamicImage1} />
        </div>
    </div>
</section>

<style lang="scss">
    @import "$lib/boilerplate/breakpoints";
    section {
        max-width: 100vw;
        overflow: hidden;
        transform: translateY(-80%);
        @include _md {
            transform: translateY(-20%) !important;
        }
    }
    @keyframes sidetoside {
        0% {
            transform: translateX(-40vw);
        }
        25% {
            transform: translateX(-60vw);
        }
        50% {
            transform: translateX(-40vw);
        }
        75% {
            transform: translateX(-20vw);
        }
        100% {
            transform: translateX(-40vw);
        }
    }
    .section-container {
        animation-name: sidetoside;
        animation-duration: 10s;
        animation-iteration-count: infinite;
        animation-timing-function: linear;
        transform: translateX(-40vw);
        display: flex;
        // width: 100%;
    }
</style>