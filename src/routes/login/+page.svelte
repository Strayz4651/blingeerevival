<script>

import {users_store} from "$lib/user";
let users = [];


import { onMount } from 'svelte';
onMount(() => {
    if($users_store.length > 2){
        users = JSON.parse($users_store);
    }
});
    

    let colors = [{namn : "Blue", value: "blå"}]
    let username = ''
    let epost = ''
    let losenord = ''
    let color = 'black'
    function handleSubmit(){
        alert("Välkommen " + username)

        
        let sameName = users.filter(user => user.username == name)
        if (sameName.length>0){
            alert("Namn är taget")
        }
        else {
            let new_user = {username: name, password: password, email: email, color: color};
            users = [...users, new_user];
            $users_store = JSON.stringify(users);
        }

    }



    
</script>

<main class='container'>

    <div style="width: 100px; height: 100px; border-radius: 50%; overflow:hidden; background-color:{color};">

    </div>
    <h1>Inloggning</h1>
        <form on:submit|preventDefault=
        {handleSubmit} action="">

        
            
<label for="name">Namn:
    <input type="text" id="name" bind:value={username} >

</label>

<br>
<label for="mail">Gmail:
    <input type="email" id="mail" bind:value={epost}>

<br>
</label>
<label for="password">Password:</label>
    <input type="password" id="password"bind:value={losenord}>


    <div> 
    </div>

<input type="submit"value="Logga in"> 



</form>

</main>

<nav><a href ="/shoppinglist">Shopping list</a></nav>

<style>
 
    main{
        background-image: url("https://t4.ftcdn.net/jpg/05/21/65/59/360_F_521655929_N80d5GaCQJ2VP073PfTXJTe9mkvsNtHE.jpg");
        background-size: cover;
        width: 100%;
        height: 100%;
        padding: 5%;
        min-width: 300px;
        min-height: 500px;
    }

    .container{
        border: solid 5px rosybrown;
        border-radius: 10px;
        width: 35%;
        height: 80%;
        min-height: 500px;
        min-width: 300px;
        background-color: #3a2e3b;
        margin: auto;
        
    }

    .container{
        display:flex;
        flex-direction: column;
        justify-content:space-evenly;
        align-items:center;
        
        
    }

</style>