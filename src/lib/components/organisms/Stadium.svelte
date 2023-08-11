<script>
	import stadium from '$lib/images/stadium.png';
</script>

<div>
    <picture>
        <img class="stadium" src={stadium} alt="Welcome" />
    </picture>
    <div class="bg-congetti">
        <div class="bg-congetti-piece"></div>
        <div class="bg-congetti-piece"></div>
        <div class="bg-congetti-piece"></div>
        <div class="bg-congetti-piece"></div>
        <div class="bg-congetti-piece"></div>
        <div class="bg-congetti-piece"></div>
        <div class="bg-congetti-piece"></div>
        <div class="bg-congetti-piece"></div>
        <div class="bg-congetti-piece"></div>
        <div class="bg-congetti-piece"></div>
        <div class="bg-congetti-piece"></div>
        <div class="bg-congetti-piece"></div>
        <div class="bg-congetti-piece"></div>
    </div>
</div>

<style lang="scss">
    @import "$lib/boilerplate/breakpoints";
    .stadium{
        width: 100%;
        height: 50vh;
    }
    div {
        width: 100vw;
        height: 60vh;
        @include _md {
            height: 50vh;
            overflow: hidden;
        }
    }
    img {
        width: 100%;
        height: 100%;
        object-fit: cover;
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

    .bg-congetti {
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

    .bg-congetti-piece {
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