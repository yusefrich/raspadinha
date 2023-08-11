<script>
    import defaultImage from '$lib/images/prize.png';
    import winGlow from '$lib/images/winGlow.png';
    import gol from '$lib/images/gol.png';
    export let pize = defaultImage;
    export let modalOpen = false;
</script>

<section>
    {#if modalOpen}
        <div on:click={()=>{modalOpen = false}} on:keypress={()=>{modalOpen = false}} aria-hidden={modalOpen} class="prize-container">
            <div class="victory-text">
                <img class="gol-golden" src={gol} alt="">
                <div class="victory-text-only">
                    <h2>VOCÊ GANHOU</h2>
                    <h1>50 reais!</h1>
                </div>
            </div>
            <div class="prize">
                <img class="slow-zoom-animation" width="100%" height="100%" src={pize} alt="">
            </div>
            <div class="glow">
                <img class="slow-rotate" width="100%" height="100%" src={winGlow} alt="">
            </div>
            <div class="confetti">
                <div class="confetti-piece"></div>
                <div class="confetti-piece"></div>
                <div class="confetti-piece"></div>
                <div class="confetti-piece"></div>
                <div class="confetti-piece"></div>
                <div class="confetti-piece"></div>
                <div class="confetti-piece"></div>
                <div class="confetti-piece"></div>
                <div class="confetti-piece"></div>
                <div class="confetti-piece"></div>
                <div class="confetti-piece"></div>
                <div class="confetti-piece"></div>
                <div class="confetti-piece"></div>
            </div>
        </div>
    {/if}
</section>

<style lang="scss">
    @import "$lib/boilerplate/breakpoints";
    .victory-text {
        z-index: 1;
        position: absolute;
        top: 0;
        left: 0;
    }
    .gol-golden {
        height: auto;
        width: 100vw;
        @include md {
            width: 70vw;
        }
        @include _md {
            top: 100px;
            position: relative;
        }
    }
    h1 {
        margin: 0;
        font-size: 6rem;
        color: #fff;
        font-family: 'Montserrat', sans-serif;
        position: relative;
        top: -1rem;
    }
    h2 {
        margin: 0;
        font-size: 2.5rem;
        color: #fff;
        font-family: 'Montserrat', sans-serif;
        position: relative;
        text-align: center;
    }
    .victory-text-only {
        position: relative;
        top: 2vh;
        @include md {
            top: -15vh;
        }
    }
    .prize-container {
        background: #000000ce;
        position: absolute;
        width: 100vw;
        height: 100vh;
        z-index: 4000;
        overflow: hidden;
        top: 0;
        left: 0;
    }
    .glow {
        position: absolute;
        bottom: 30vh;
        height: auto;
        transform: translate(50%, 50%);
        width: 400vw;
        right: 50vw;
        @include md {
            right: 20vw;
            width: 150vw;
        }
    }
    .prize {
        overflow: hidden;
        position: absolute;
        bottom: 30vh;
        z-index: 1;
        border-radius: 100%;
        height: auto;
        transform: translate(50%, 50%);
        -webkit-box-shadow: 0px 0px 95px 28px rgba(235,197,44,1);
        -moz-box-shadow: 0px 0px 95px 28px rgba(235,197,44,1);
        box-shadow: 0px 0px 95px 28px rgba(235,197,44,1);
        width: 50vw;
        right: 50vw;
        @include md {
            right: 20vw;
            width: 17vw;
        }
    }

    /* confette css */
    $yellow: #ffd300;
    $blue: #17d3ff;
    $pink: #ff4e91;

    $duration: 1000;

    @function randomNum($min, $max) {
        $rand: random();
        $randomNum: $min + floor($rand * (($max - $min) + 1));

        @return $randomNum;
    }

    .icon {
        font-size: 32px;
        font-weight: bold;
        letter-spacing: 32px;
        position: relative;
    }

    .confetti {
        display: flex;
        justify-content: center;
        align-items: center;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 200px;
        overflow: hidden;
    }

    .confetti-piece {
        position: absolute;
        width: 8px;
        height: 16px;
        background: $yellow;
        top: 0;
        opacity: 0;
    
        @for $i from 1 through 13 {
            &:nth-child(#{$i}) {
                left: $i * 7%;
                transform: rotate(#{randomNum(-80, 80)}deg);
                animation: makeItRain $duration * 1ms infinite ease-out;
                animation-delay: #{randomNum(0, $duration * .5)}ms;
                animation-duration: #{randomNum($duration * .7, $duration * 1.2)}ms
            }
        }
        
        &:nth-child(odd) {
            background: $blue;
        }
        
        &:nth-child(even) {
            z-index: 1;
        }
        
        &:nth-child(4n) {
            width: 5px;
            height: 12px;
            animation-duration: $duration * 2ms;
        }
        
        &:nth-child(3n) {
            width: 3px;
            height: 10px;
            animation-duration: $duration * 2.5ms;
            animation-delay: $duration * 1ms;
        }
        
        &:nth-child(4n-7) {
            background: $pink;
        }
    }

    @keyframes makeItRain {
        from {
            opacity: 0;
        }
        
        50% {
            opacity: 1;
        }
        
        to {
            transform: translateY(200px);
        }
    }
</style>