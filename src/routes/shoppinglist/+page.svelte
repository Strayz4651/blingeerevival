<script>
    let varor = $state([
        {name: "Chips", köpt: true},
        {name: "Kyckling", köpt: true},
        {name: "Juice", köpt: true},
        {name: "Apelsin", köpt: true},
        {name: "Vindruvor", köpt: true},
        {name: "Frukt", köpt: false},
        {name: "Godis", köpt: false},
        {name: "Kött", köpt: false},
        {name: "Sallad", köpt: false},
        {name: "Flingor", köpt: false},
    ]);

    let nyVara = $state("");

    function läggTillVara() {
        if (nyVara.trim() === "") return;
        varor.push({ name: nyVara, köpt: false });
        nyVara = "";
    }

    function taBortVara(index) {
        varor.splice(index, 1);
    }
    
    function toggleKöpt(vara) {
        vara.köpt = !vara.köpt;
    }
</script>

<main class="container">
    <h1>Shoppinglist</h1>

    <div class="categories_container">

        <section>
            <h2>Köpt</h2>
            <ul>
                {#each varor as vara, index}
                    {#if vara.köpt}
                        <li onclick={() => toggleKöpt(vara)}>
                            {vara.name}
                            <button onclick={(e) => { e.stopPropagation(); taBortVara(index); }}>
                                Ta bort
                            </button>
                        </li>
                    {/if}
                {/each}
            </ul>
        </section>

        <!-- Ej köpta varor -->
        <section>
            <h2>Att köpa</h2>
            <ul>
            {#each varor as vara, index}
                {#if !vara.köpt}
                    <li onclick={() => toggleKöpt(vara)}>
                        {vara.name}
                        <button onclick={(e) => { e.stopPropagation(); taBortVara(index); }}>
                            Ta bort
                          </button>
                    </li>
                    {/if}
                {/each}
            </ul>
        </section>
    </div>

    <div style="text-align:center; padding:10px;">
        <input 
            bind:value={nyVara}
            placeholder="Lägg till vara..."
        >
        <button onclick={läggTillVara}>Lägg till</button>
    </div>
</main>

<style>
.container{
    display:grid; 
    grid-template-rows: 1fr 8fr 1fr;
    margin: auto;
    background-color: rgb(231, 0, 158);
    width: 60vw;
    height: 70vh;
    border-radius: 10px;  
}

.categories_container{
    background-color: rgb(251, 111, 181);
    grid-template-columns: 1fr 1fr;
    width:100%;
    display: grid;
    justify-items: center;
}

section{
    width: 80%;
}

.container h1 {
    justify-self: center;
    align-self: center;
    background-color: rgb(120, 2, 75, 0.379);
}

.container h2:first-child{
    background-color: rgba(120, 2, 75, 0.379);
}

.categories_container section:first-child{  
    background-color: rgba(255, 0, 153, 0.249);
    font-size: 20px;
    text-align: center;
}

.categories_container section:last-child{  
    background-color: rgba(211, 1, 148, 0.3);
    font-size: 20px;
    text-align: center;
}
</style>
