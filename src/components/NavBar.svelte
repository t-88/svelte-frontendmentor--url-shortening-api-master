<nav>
        {#if width >= 700 }
            <section class="left">
                <img src="../assets/logo.svg" alt="logo">
                <div class="urls">
                    <p>Features</p>
                    <p>Pricing</p>
                    <p>Resources</p>
                </div>
            </section>
            <section class="right">
                <Button text="Login"/>
                <Button text="Sign Up"/>
            </section>
        {:else}
            <img src="../assets/logo.svg" alt="logo">
            <div class="mobile-nav">
                <img src="../assets/hamburger.svg" on:click={() => {isShown = !isShown}}>
                {#if isShown}
                    <div transition:slide class="container">
                        <p>Features</p>
                        <p>Pricing</p>
                        <p>Resources</p>
                        <hr/>
                        <Button text="Login" _class="login-btn"/>
                        <Button text="Sign Up" theme={1}/>
                    </div>
                {/if}
            </div>
        {/if}

</nav>
<svelte:window bind:innerWidth={width}/>
<script lang="ts">
    import Button from "./ui/Button.svelte"
    import { slide } from 'svelte/transition';

    let width:number
    let isShown:Boolean = false
</script>

<style type="text/scss">
    @import "../shared";
    nav {
        display: flex;
        justify-content: space-between;
        section{
            display: flex;
        }
        .left {
            align-items: center;
            img {
                height: min-content;
            }
            .urls {
                display: flex;
                align-items: center;
                color: hsl(0, 0%, 75%);
                p {
                    flex: 1;
                }

                p:hover {
                    color: hsl(257, 27%, 26%);
                    font-weight: 700;
                    cursor: pointer;
                }
            }
        }

    }
    @include media(">=tablet") {
        $max-w: $pc;
        $min-w: $tablet;
        nav {
            font-size: applyMath(16,14,$max-w,$min-w);
            .left {
                gap: applyMath(50,30,$max-w,$min-w);
            }
            .urls {
                gap: applyMath(30,15,$max-w,$min-w);
                width: applyMath(290,0,$max-w,$min-w);               
            }

            .right {
                gap: applyMathO(20,10,$max-w,$min-w);
                :global(button) {
                    font-size: applyMath(16,13,$max-w,$min-w) !important;
                    padding:  applyMath(8,0,$max-w,$min-w)  applyMath(20,15,$pc,$tablet);
                }
            }
        }
    }
    @include media("<tablet") {
        $max-w: $tablet;
        $min-w: $phone;
        nav {
            position: relative;
            img {
                width: min-content;
                height: min-content;
            }
            .mobile-nav {
                align-self: flex-end;
            }
            .container {
                display: flex;
                flex-direction: column;
                align-items: center;
                position: absolute;
                text-align: center;
                top: 0;
                left: 5%;
                background-color: #3b3054;
                width: 90%;
                padding: 20px 20%;
                color: white;
                font-weight: 700;
                border-radius: 10px;
                font-size: 18px;
                gap: 10px;
                transform: translateY(55px);
                z-index: 10;
                hr {
                    border: transparent;
                    width: 100%;
                    background: #ffffff33;
                    height: 1px;
                }
                :global(button) {
                    width: fit-content;
                    font-weight: 700;
                    font-size: 18px;
                }
                :global(.login-btn){
                    color: white !important;
                    font-size: 18px;
                }
            }
        }
    }
</style>