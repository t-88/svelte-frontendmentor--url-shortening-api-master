<div id="BoostLinks-comp">
    <h1>Boost your links today</h1>
    <a href="#ShortenBox-comp">
        <Button text="Get Started" theme={1}/>
    </a>
</div>

<script lang="ts">
    import Button from "./ui/Button.svelte";
</script>

<style type="text/scss">
    @import "../shared";
    #BoostLinks-comp {
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
        background-image: url("../assets/bg-boost-desktop.svg");
        gap: 20px;
        background-color: hsl(257, 27%, 26%);
        color: white;
        padding: 40px 0;
        :global(button) { width: fit-content; }
    }
    @include media(">=tablet") {
        $max-w: $pc;
        $min-w: $tablet;
        #BoostLinks-comp {
            background-size: applyMath(1803,800,$max-w,$min-w) 100%;
            h1 { font-size: applyMath(50,35,$max-w,$min-w); }
            :global(button) {
                padding: 10px 35px;
                font-size: 18px;
            }
        }
    }
    @include media("<tablet",">phone") {
        $max-w: $tablet;
        $min-w: $phone;
        #BoostLinks-comp {
            background-size: applyMath(1803,800,$max-w,$min-w) 100%;
            h1 { font-size: applyMath(35,25,$max-w,$min-w); }
            :global(button) { font-size:  applyMath(18,19,$max-w,$min-w); }
        }
    }
    @include media("<=phone") {
        #BoostLinks-comp {
            background-size: 800px 100%;
            h1 { font-size: 25px; }
            :global(button) { font-size:  19px; }
        }
    }
    
</style>