<script>
    import Model from "./Model.svelte";

    let showModel = false
    

</script>
<div class="additio">
    <button on:click={() => (showModel = !showModel)}>Add Developer</button>
    {#if showModel}
        <Model on:close={() => (showModel = false)} />
    {/if}
</div>

<style>
    button {
        border: none;
        background-color: #000070;
        padding: 0.5rem 1rem;
        border-radius: 0.5rem;
        color: #fff;
        cursor: pointer;
    }
</style>