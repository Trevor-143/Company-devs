<script>
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher()

    function close() {
        dispatch("close")
    }

</script>

<div class="addForm" >
    <form>
        <input type="text" placeholder="name">
        <input type="email" placeholder="email">
        <input type="text" placeholder="position">
        <div class="radios">
            <h3>Working?</h3>
            <input type="radio" name="status">
            <input type="radio" name="status">
        </div>
        <div class="btns">
            <button>Add Developer</button>
            <button on:click={close} >Close</button>
        </div>
    </form>
</div>

<style>
    .addForm {
        position: fixed;
        bottom: 0;
        right: 0;
        z-index: 10;
        margin-right: 5%;
        margin-bottom: 5%;
    }
    .addForm form {
        background-color: #fff;
        display: flex;
        flex-direction: column;
    }
</style>