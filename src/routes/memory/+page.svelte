<script>
    let cards = $state([0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 9, 9])
    let bluePoints = 0
    let redPoints = 0

</script>
<h1>Memory</h1>

<aside>
    <p>{redPoints}</p>
</aside>

<aside2 class="blue">
    <p>{bluePoints}</p>
</aside2>

<main>
    <div class="grid-container">
        {#each cards as card}
        <div class='card'>{card}
            <img class="front"src="https://i.pinimg.com/236x/8b/be/a7/8bbea75116b2852a163c9dd64049d76d.jpg" alt=" ">
            <img class="back"src="https://i.pinimg.com/736x/4e/b2/fa/4eb2fac3d011fc2257ad28e580f6b4a5.jpg" alt=" ">
        </div>
        
            
        {/each}

    </div>
       
</main>



<style>

.grid-container{
    display: grid;
    grid-template-columns:repeat(3, 150px);
    grid-template-rows: repeat(5,150px);
    gap:5px;
    
   

}

.card{
    background-color: rgb(24, 15, 33);
    border-radius: 3px;
    border-color: rgb(0, 0, 0);
    position: relative;
    overflow: hidden; 
}


.card img {
    height: 100%;
    width: 100%;
    position: absolute;
    
}



aside{
    width: 100px;
    height: 100px;
    position: fixed;
    bottom: 10px;
    right: 10px;
    background-color: red;
    display: flex;
    justify-content: center;
    align-items: center;
  }

p{
    font-size: 30px;
  }
                          
aside2{
    width: 100px;
    height: 100px;
    position: fixed;
    bottom: 10px;
    left: 10px;
    background-color: blue;
    display: flex;
    justify-content: center;
    align-items: center;
  }


.front{
    z-index: 2;
}

.back{
    z-index: 1;
    
}

</style>