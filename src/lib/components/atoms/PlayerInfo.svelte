<script>
    import defaultCoin from '$lib/images/coin.png';
    import defaultBall from '$lib/images/ball.png';
</script>

<section>
    <div>
        <img src={defaultCoin} alt="coin" />
        <h3>R$ 100,00</h3>
    </div>
    <div class="reverse-mobile">
        <img src={defaultBall} alt="soccer ball" />
        <h2>15</h2>
    </div>
</section>

<style lang="scss">
    @import "$lib/boilerplate/breakpoints";
    div {
        display: flex;
    }
    .reverse-mobile{
        @include _md {
            flex-direction: row-reverse;
        }
    }
    h3 {
        margin: 0;
        font-family: 'Montserrat', sans-serif;
        font-weight: 800;
        padding-top: 1vh;
        letter-spacing: -0.1rem;
        color: white;
        font-size: 6vw;
        text-shadow: 0px 0px 10px #333;
        @include md {
            font-size: 2.8vw;
        }
    }
    h2 {
        margin: 0;
        font-family: 'Montserrat', sans-serif;
        font-weight: 800;
        // padding-top: 4px;
        letter-spacing: -0.1rem;
        color: white;
        text-shadow: 0px 0px 10px #333;
        font-size: 6vw;
        @include md {
            transform: translateY(-5px);
            font-size: 3.4vw;
        }
        @include _md {
            padding-top: 1vh;
        }
    }
    section {
        position: absolute;
        left: 7vw;
        @include md {
            bottom: 2vh;
        }
        @include _md {
            top: 20px;
            left: 20px;
            display: flex;
            justify-content: space-between;
            width: calc(100vw - 40px);
        }
        z-index: 1001;
    }
    img {
        width: auto;
        height: 10vw;
        @include md {
            height: 4vw;
        }
    }
</style>
