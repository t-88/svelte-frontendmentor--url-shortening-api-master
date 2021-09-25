<div class="IconTextCard-comp {_class}" >
    <div class="img-container">
        <img src={data.path} alt="icon">
    </div>
    <h1 class="title">{data.title}</h1>
    <p class="description">{data.description}</p>
</div>

<script lang="ts">
    export let data:Object;
    export let _class:string = "" 
</script>

<style type="text/scss">
    @import "../../shared";

    .IconTextCard-comp{
        display: flex;
        flex-direction: column;
        position: relative;
        gap: 20px;
        height: fit-content;
        background: white;
        box-shadow: #0000000d 0 0 3px 0;
        border-radius: 5px;
        .img-container {
            display: flex;
            align-items: center;
            justify-content: center;
            background: hsl(257, 27%, 26%);
            border-radius: 100%;
            position: absolute;
        }
        h1 {
            color: hsl(260, 8%, 14%);
        }
        p {
            color: hsl(257, 7%, 63%);
        }
    }
    @include media(">=tablet") {
        $min-w: $tablet; 
        $max-w: $pc;
        .IconTextCard-comp {
            width: applyMath(390,230,$max-w,$min-w);
            font-size: applyMath(18,12,$max-w,$min-w);
            padding: 60px applyMath(20,10,$max-w,$min-w) 20px;

            .img-container {
                $width: 75px;
                width: $width;
                height: $width;
                top: calc(-#{$width} / 2);
            }
        }
    }
    @include media("<tablet") {
        $max-w: $tablet;
        $min-w: $phone; 
        .IconTextCard-comp {
            width: 340px;
            font-size: 18px;
            text-align: center;
            padding: 60px 10px 20px;
        
            .img-container {
                $width: 80px;
                width: $width;
                height: $width;
                top: calc(-#{$width} / 2);
                left: 130px;
            }
        }
    }
</style>