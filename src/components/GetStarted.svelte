<div class="GetStarted-comp">
    <section class="text">
        <h1>More than just shorter links</h1>
        <p>
            Build your brand’s recognition and get detailed insights 
            on how your links are performing.
        </p>
        <a href="#ShortenBox-comp">
            <Button text="Get Started" theme={1}/>
        </a>
    </section>
    <img src="../assets/illustration-working.svg" alt="illustration-working">
</div>

<script lang="ts">
    import Button from "./ui/Button.svelte";
</script>

<style type="text/scss">
    @import "../shared";
    .GetStarted-comp {
        display: flex;
        align-items: center;
        justify-content: space-between;
        width: fit-content;
        h1 {
            color: hsl(255, 11%, 22%);
            line-height: 1.13;
        }
        p {
            font-size: 22.8px;
            color: hsl(257, 7%, 63%);
            margin-bottom: 20px;
        }

        :global(button) {
            font-size: 17px;
            padding: 10px 30px;
        }
    }
    @include media(">=tablet") {
        $max-w: $pc;
        $min-w: $tablet;
        .GetStarted-comp {
            margin-top: applyMath(80,20,$max-w,$min-w);

            .text {
                width: applyMath(600,340,$max-w,$min-w);
                h1 { font-size: applyMath(80,45,$max-w,$min-w); }
                p { font-size: applyMath(22.8,14,$max-w,$min-w); }
            }
            img {
                width: applyMath(900,480,$max-w,$min-w);
                transform: translate(applyMath(150,0,$max-w,$min-w), 0);
            }
        }
    }
    @include media("<tablet") {
        .GetStarted-comp { 
            flex-direction: column-reverse;
            align-items: center;
            justify-content: center;
            width: 100%;
            .text {
                text-align: center;
                p {
                    margin-top: 15px;
                }
            }
        }
    }
    @include media("<tablet",">phone") {
        $max-w: $tablet;
        $min-w: $phone;
        .GetStarted-comp {
            .text {
                width: applyMath(340,290,$max-w,$min-w);
                h1 { font-size: applyMath(45,38,$max-w,$min-w); }
                p { font-size: applyMath(18,16,$max-w,$min-w); }
            }
            img {
                width: applyMath(500,440,$max-w,$min-w);
                transform: translate(applyMath(60,70,$max-w,$min-w), 0);
            }
        }
    }
    @include media("<=phone") {
        .GetStarted-comp {
            .text {
                width: 290px;
                h1 { font-size: 38px; }
                p { font-size: 16px; }
            }
            img {
                width: 440px;
                transform: translate(70px, 0);
            }
        }
    }
</style>