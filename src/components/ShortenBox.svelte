<div id="ShortenBox-comp">
    <input placeholder="Shorten a link here..." class:isNotValid bind:value={shortenUrl} >
    {#if isNotValid}
        <p>Please add a link</p>
    {/if}
    <Button text="Shorten It!" theme={1} onClick={SubmitUrl}/>
</div>

<script lang="ts">
    import Button from "./ui/Button.svelte"
    let shortenUrl = ""
    let isNotValid = true

    $: {
        shortenUrl
        isNotValid = false
    }

    function isValidURL(string) {
        var res = string.match(/(http(s)?:\/\/.)?(www\.)?[-a-zA-Z0-9@:%._\+~#=]{2,256}\.[a-z]{2,6}\b([-a-zA-Z0-9@:%_\+.~#?&//=]*)/g);
        return (res !== null)
    };
    const SubmitUrl = () => {
        isNotValid = !isValidURL(shortenUrl)
        if(isNotValid) {
            shortenUrl = ""
            setTimeout(() => {
                isNotValid = true
            },1)
        } 
    }
    
</script>

<style type="text/scss">
    @import "../shared";
    #ShortenBox-comp {
        background-color: #3b3054;
        display: flex;
        border-radius: 5px;
        justify-content: space-between;
        gap: 20px;
        margin-top: 50px;
        position: relative;
        background-image: url("../assets/bg-shorten-desktop.svg");

        input {
            border: transparent;
            outline: none;
            flex: 1;
            border-radius: 8px;
        }
        .isNotValid {
            border: solid 3px hsl(0, 87%, 67%);
            color: hsl(0, 87%, 67%);
            &::placeholder {
                color: hsl(0, 87%, 67%);
            }
        }
        p {
            position: absolute;
            bottom: 10px;
            font-style: italic;
            color: hsl(0, 87%, 67%);
            font-size: 14px;
        }
        :global(button) {
            border-radius: 8px ;
            padding: 10px 25px;
        }
    }
    @include media(">=tablet") {
        $max-w: $pc;
        $min-w: $tablet;
        #ShortenBox-comp {
            padding: 40px 50px;
            background-size: applyMath(1490,870,$max-w,$min-w) applyMath(250,300,$max-w,$min-w);
            background-position: applyMath(-50,-130,$max-w,$min-w) applyMath(-20,-40,$max-w,$min-w);
            input {
                font-size: 15px;
                padding: 10px 20px;
            }
        }
    }
    @include media("<=550px") {
        $max-w: 550;
        $min-w: $phone;
        #ShortenBox-comp {
            flex-direction: column;
            background-size: 490px 200px;
            background-position: 0 0;
        }
    }
    @include media("<tablet") {
        #ShortenBox-comp {
            background-size: 870px 300px;
            background-position: -130px -40px;
            input { font-size: 13px; }
            :global(button) { font-size: 15px; }    
        }
    }
    @include media("<tablet",">phone") {
        $max-w: $tablet;
        $min-w: $phone;
        #ShortenBox-comp {
            padding: applyMath(40,20,$max-w,$min-w) applyMath(50,20,$max-w,$min-w);
            input { padding: 10px applyMath(20,15,$max-w,$min-w); }
        }
    }
    @include media("<=phone") {
        #ShortenBox-comp {
            padding: 20px 20px;
            input { padding: 10px 15px; }
        }
    }
    
</style>