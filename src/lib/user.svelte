<script>
    import { createEventDispatcher } from "svelte";

    export let user;
    export let i;

    const dispatch = createEventDispatcher()

    const remove = () => {
        dispatch("remove", user.id)
    }

</script>

<div class="user" style:background-color={ user.active == true ? "#a9ffca" : "#ffbcbc" } >
    <p> {i+1} </p>
    <img src={user.image} alt={user.name}>
    <div class="userMiniInfo">
        <h3> {user.name} </h3>
        <h4> {user.email} </h4>
        <h4> {user.position} </h4>
    </div>
    <button on:click={remove} > Remove Developer </button>
</div>

<style>
    .user {
        display: flex;
        align-items: center;
        justify-content: flex-start;
        background-color: #ffbcbc;
        padding: 1rem;
        border-radius: 1rem;
        border: #e0e0e0 solid 2px;
        transition: 0.5s;
        position: relative;
    }
    .user p {
        position: absolute;
        top: 0;
        right: 0;
        margin-top: 10px;
        margin-right: 10px;
        background-color: #000070;
        color: #fff;
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 0.5rem;
        font-weight: 700;
        padding: 0.2rem 0.5rem;
    }
    .user:hover {
        background-color: rgba(224, 224, 224, 0);
    }
    .user:hover button {
        opacity: 1;
    }
    .user img {
        width: 40px;
        border-radius: 50%;
    }
    .user .userMiniInfo {
        padding: 1rem;
        font-size: 0.8rem;   
    }
    .user button {
        position: absolute;
        border: none;
        background-color: #b90000;
        color: #fff;
        border-radius: 0.5rem;
        padding: 0.5rem 1rem;
        bottom: 0;
        right: 0;
        margin-bottom: -10px;
        margin-right: 10px;
        transition: 0.4s;
        opacity: 0;
        cursor: pointer;
    }

    h4 {
        font-weight: 400;
        color: rgb(65, 65, 65);
    }
</style>