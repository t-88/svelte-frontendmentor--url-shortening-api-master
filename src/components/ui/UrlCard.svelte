<div class="UrlCard-comp">
    <p class="p">{url.original}</p>
    <section class="right">
        <a class="p url" href={url.created} target="_blank">{url.created}</a>
        <Button _class={isCopy == true ? "copied" : ""} 
                text={isCopy == false ? "Copy" : "Copied!"}  
                theme={1} onClick={() => {isCopy = !isCopy;}}/>
    </section>
</div>

<script lang="ts">
    import Button from "./Button.svelte"
    
    export let url:Object = {}
    let isCopy = false
</script>

<style type="text/scss">
    .UrlCard-comp {
        display: flex;
        align-items: center;
        box-shadow: #0000000d 0 0 3px 0;
        padding: 15px 25px;
        background: white;
        .p {
            flex: 1;
            text-decoration: none;
            color: black;
        }
        .right {
            display: flex;
            align-items: center;
            gap: 20px;
            .url {
                color: hsl(180, 66%, 49%);
            }
        }
        :global(button) {
            border-radius: 5px;
            padding: 8px 0;
            width: 97px;
            font-size: 14px;
        }
        :global(.copied) {
                background-color:hsl(257, 27%, 26%) !important;
        }
    }
</style>