<script>
    import Image from "../assets/dev.png"
    import PC from "../assets/pc.png"
    import NewUser from "./NewUser.svelte";
    import User from "./user.svelte"
    
    let users = [
        {
            id: 1,
            image: Image,
            name: "Trevor",
            email: "trevor@gmail.com",
            position: "Front-End Developer",
            active: true
        },
        {
            id: 2,
            image: Image,
            name: "Travis",
            email: "travis@gmail.com",
            position: "Back-End Developer",
            active: false
        },
        {
            id: 3,
            image: Image,
            name: "Morris",
            email: "morris@gmail.com",
            position: "Back-End Developer",
            active: true
        },
        {
            id: 4,
            image: Image,
            name: "Arapu",
            email: "arapu@gmail.com",
            position: "Front-End Developer",
            active: true
        },
        {
            id: 5,
            image: Image,
            name: "Wiwa",
            email: "wiwa@gmail.com",
            position: "Back-End Developer",
            active: false
        },
    ]

    $: filteredUsers = users;
    

    const filter = (e) => {
        // console.log(e.target.value)
        if (e.target.value == "null") {
            return filteredUsers = users
        } else {
            const selected = e.target.value == "true"
            filteredUsers = users.filter((user) => user.active == selected)
        }
    }

    const remove = ({detail}) => {
        // console.log(detail)
        users = users.filter((user) => user.id != detail)
    }
    
</script>
    
<div class="users">

    <h1>Company Developers</h1>

    <div class="top">
        <select name="userlist" on:change={filter}>
            <option value={null}> All Developers </option>
            <option value={true}> Active </option>
            <option value={false}> Inactive </option>
        </select>
        
        <NewUser />
    </div>

    <div class="userList">
    {#each filteredUsers as user, i(user.id) }
        <User {user} {i} on:remove = {remove} />
    {:else}
        <div class="else">
            <img src={PC} alt="brocken pc">
            <h1>Hey, The company has no Developers at the moment.</h1>
        </div>
    {/each}  
    </div>

</div>
    
<style >
    .users {
        margin: 2rem 0;
    }
    .users h1 {
        margin-bottom: 1rem;
        font-size: 1rem;
        margin-left: 1rem;
    }

    .userList {
        display: grid;
        gap: 2rem;
        grid-template-columns: repeat(auto-fit, minmax(15rem, 1fr));
    }

    .else {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 60vh;
    }
    .else img {
        width: 100px;
        margin: 2rem;
    }
    .else h1 {
        font-size: 0.9rem;
        color: rgb(41, 41, 41);
        text-align: center;
    }
    .top {
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        justify-content: space-between;
        margin: 1rem;
    }
    /* Style the select box */
    select {
        padding: 10px;
        border: none;
        padding: 0.5rem 1rem;
        border-radius: 0.5rem;
        outline: none;
        background-color: #e0e0e0;
    }
</style>