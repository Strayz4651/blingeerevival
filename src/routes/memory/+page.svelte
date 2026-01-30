<script>

    let cards = $state([])

    let cardimgs = [
        "https://i.pinimg.com/originals/83/59/19/83591999955c26f0e42daf1dd350655d.jpg",
        "https://i.pinimg.com/736x/b3/0a/8a/b30a8a62ad4e0178250b37be3c8f1732.jpg",
        "https://i.pinimg.com/564x/9e/a8/e6/9ea8e6d974eaf253caf5cde31785d0c5.jpg",
        "https://i.pinimg.com/236x/a2/c4/59/a2c4596c77acfa91760bbb6495660a0e.jpg",
        "https://i.pinimg.com/236x/8b/9b/43/8b9b43c43a5b63d4862e3c50304c6c5b.jpg",
        "https://w0.peakpx.com/wallpaper/577/397/HD-wallpaper-evil-skull-awesome-skeleton.jpg"
    ]

    
    let deck = [...cardimgs, ...cardimgs]

    
    for (let i = deck.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1))
        ;[deck[i], deck[j]] = [deck[j], deck[i]]
    }

    
    cards = deck.map(img => ({
        flipped: false,
        matched: false,
        img
    }))
    

    let bluePoints = 0
    let redPoints = 0
    let blueTurn = $state(false)
    let flipcount = 0

    function flip(card) {

    if (card.flipped || card.matched) return
    if (cards.filter(c => c.flipped && !c.matched).length === 2) return

    card.flipped = true

    let flippedCards = cards.filter(c => c.flipped && !c.matched)

    if (flippedCards.length === 2) {

        if (flippedCards[0].img === flippedCards[1].img) {
            flippedCards.forEach(c => c.matched = true)

            if (blueTurn) bluePoints++
            else redPoints++

            blueTurn = !blueTurn
        }
       
        else {
            setTimeout(() => {
                flippedCards.forEach(c => c.flipped = c.matched)
                cards = cards
                blueTurn = !blueTurn
            }, 800)
        }
    }
}

</script>

<h1>Memory</h1>

<aside>
    <p>{redPoints}</p>
</aside>

<aside class="blue">
    <p>{bluePoints}</p>
</aside>

<aside class="turn" class:blue= { blueTurn }>
    
</aside>

<main>
    <div class="grid-container">
        {#each cards as card}
        <div class='card' class:flipped={card.flipped } 
        onclick={() => flip(card)}>
            <img class="front"src="https://opengameart.org/sites/default/files/card%20back%20red.png" alt=" ">
            <img class="back"src={card.img}>
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
    transform-style: preserve-3d;
    transition: transform 0.5s;
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
                          
.blue{
    left: 10px;
    background-color: blue;
  }

.turn{
    box-shadow: 0 0 10px 10px yellowgreen;
    z-index: -1;
}

.front{
    z-index: 2;
    transform: rotateY(0deg);
    transform: rotate(90deg);
    backface-visibility: hidden;

}

.back{
    z-index: 2;
    transform: rotateY(180deg);
    backface-visibility: hidden;


}
.flipped{
        transform: rotateY(180deg);
}

</style>