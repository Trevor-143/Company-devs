<script>
    import { createEventDispatcher } from "svelte";
    import Model from "./Model.svelte";
    const dispatch = createEventDispatcher()

    let showModel = false

    let newDev = {}
    
    const handleForm = (e) => {
        // console.log(e)
        // console.log(newDev)
        dispatch("addDev", newDev)
    }

</script>
<div class="additio">
    <button on:click={() => (showModel = !showModel)}>Add Developer</button>
    {#if showModel}
        <Model
            on:close={() => (showModel = false)}
            on:submit={handleForm} > 
            <input type="text" placeholder="name" bind:value={newDev.name}>
            <input type="email" placeholder="email" bind:value={newDev.email}>
            <input type="text" placeholder="position" bind:value={newDev.position}>
            <div class="radios">
                <h3>Are the Active ?</h3>
                <div class="radioBtns">
                    <input type="radio" name="status" value={true} bind:group={newDev.status} >
                    <input type="radio" name="status" value={false} bind:group={newDev.status} >
                </div>
            </div>
        </Model>
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

    input {
        background-color: #e0e0e0;
        border: none;
        padding: 0.5rem 1rem;
        border-radius: 0.5rem;
        outline: 1rem;
        margin-bottom: 1rem;
    }
    .radios {
        display: flex;
        justify-content: space-between;
        align-items: center;
        color: #fff;
        background-color: #000070;
        padding: 0.5rem 1rem;
        border-radius: 0.5rem;
    }
    .radios h3 {
        font-size: 0.9rem;
    }
    
    .radioBtns input {
        cursor: pointer;
    }
</style>