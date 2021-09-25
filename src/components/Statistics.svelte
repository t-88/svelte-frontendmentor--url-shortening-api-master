<div id="Statistics-comp">
    <section class="top">
        <h1>Advanced Statistics</h1>
        <p>
            Track how your links are performing across the web with our 
            advanced statistics dashboard.
        </p>
    </section>
    <section class="bottom">
        <div class="bg-rect" />
        {#each cardData as data, index}
            <IconTextCard _class="card-{index}" {data}/>
        {/each}
    </section>
</div>

<script lang="ts">
    import IconTextCard from "./ui/IconTextCard.svelte"
    let cardData:Object[] = [
        {path: "../../assets/icon-brand-recognition.svg",title: "Brand Recognition",description: "Boost your brand recognition with each click. Generic links don’t mean a thing. Branded links help instil confidence in your content."},
        {path: "../../assets/icon-detailed-records.svg",title: "Detailed Records",description: "Gain insights into who is clicking your links. Knowing when and where people engage with your content helps inform better decisions."},
        {path: "../../assets/icon-fully-customizable.svg",title: "Fully Customizable",description: "Improve brand awareness and content discoverability through customizable links, supercharging audience engagement."}
    ]
</script>

<style type="text/scss">
    @import "../shared";
    #Statistics-comp {
        display: flex;
        flex-direction: column;
        margin-top: 100px;
        gap: 120px;

        .top {
            text-align: center;
            align-self: center;
            display: flex;
            flex-direction: column;
            gap: 10px;
            h1 { color: hsl(260, 8%, 14%); }
            p { color: hsl(257, 7%, 63%); }
        }
        .bottom {
            display: flex;
            justify-content: space-between;
            position: relative;
            .bg-rect {
                background:#30cecc;
                position: absolute;
                width: 10px;
                top: 150px;
            }
        }
    }

    @include media(">=tablet") {
        $max-w: $pc;
        $min-w: $tablet;
        #Statistics-comp {
            .top {
                width: 600px;
                h1 { font-size: applyMath(40,30,$max-w,$min-w); }
                p { font-size: applyMath(18,17,$max-w,$min-w); }
            }
            .bottom {
                gap: applyMath(0,20,$max-w,$min-w);
                height: applyMath(350,280,$max-w,$min-w);
                .bg-rect { width: 100%; height: 10px;}
                :global(.card-1) { align-self: center; }
                :global(.card-2) { align-self: flex-end; }
            }
        }
    }
    @include media("<tablet") {
        #Statistics-comp .bottom{
            flex-direction: column;
            height: fit-content;
            align-items: center;
            gap: 80px;
            .bg-rect { height: 60%; }
        }    
    }
    @include media("<tablet",">phone") {
        $max-w: $tablet;
        $min-w: $phone;
        #Statistics-comp .top {
            width: applyMath(600,310,$max-w,$min-w);
            h1 { font-size: applyMath(30,27,$max-w,$min-w); }
            p { font-size: applyMath(17,17,$max-w,$min-w); }
        }               
    }
    @include media("<=phone") {
        #Statistics-comp .top{
            width: 310px;
            h1 { font-size: 27px; }
            p { font-size: 17px; }
        }
    }
</style>
