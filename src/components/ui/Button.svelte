<button style={elementStyle} class={_class} 
                            on:mouseenter={() => {state = "hover"}} 
                             on:mouseleave={() => {state = "idle"}} 
                             on:click={onClick}>
    {text}
</button>

<script lang="ts">
    export let text: string;
    export let onClick = ():void => {}
    export let _class:string = ""

    let state:string = "idle"
    export let theme:number = 0
    export let idleBgColor: string[] = ["transparent","hsl(180, 66%, 49%)"]
    export let hoverBgColor:string = "hsl(178deg 58% 74%)"
    export let idleTextColor: string[] = ["hsl(257, 27%, 26%)","white"]
    export let hoverTextColor:string = "white"

    

    let currBgColor:string
    let currTextColor:string
    let elementStyle:string 

    const onMouseEnter = ():void => {
        currBgColor = hoverBgColor
        currTextColor = hoverTextColor
    }
    const onMouseLeave = ():void => {
        currBgColor = idleBgColor[theme]
        currTextColor = idleTextColor[theme]
    }

    $: {
        state == "idle" ? onMouseLeave() : onMouseEnter()
        elementStyle =
        `
            background: ${currBgColor};
            color: ${currTextColor};
        `
    }
        
</script>

<style type="text/scss">
    button {
        font-size: 15px;
        padding: 8px 20px;
        border-radius: 500px;
        border: transparent;
        cursor: pointer;
    }
</style>