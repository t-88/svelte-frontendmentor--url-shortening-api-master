<div id="UrlList-comp">
    <p>API doesn't work</p>
    <!--
        {#each  urlList as url }
            <UrlCard {url} />    
        {/each}
    -->

</div>

<script lang="ts">
    import UrlCard from "./ui/UrlCard.svelte"
    export let urlList:Object[];
</script>

<style type="text/scss">
    #UrlList-comp {
        margin-top: 40px;
        text-align: center;
        font-size: 20px;
        color: hsl(0, 87%, 67%);;
    }
</style>