<script>
    import ElizaBot from 'elizabot'

    import { enhance } from "$app/forms";

    const eliza = new ElizaBot();

    
    async function write(message) {
        //TODO: Add the new message to the chat


        // random delay for Eliza's response time
        await new Promise((r) => setTimeout(r, 1000 + Math.random() * 1000));

        //TODO: Add Eliza's response to the chat

    }

    
    
                

    let chat = $state([{ user: 'Eliza', message: eliza.getInitial() }]);
</script>

<main>

    <section>
        <article>
            {#each chat as c}
                <p>{c.user, c.message}</p>
            {/each}
        </article>
        <article id="visible"></article>
    </section>

    <form method="post"
    use:enhance={({ formElement, formData, action, cancel }) => {
      cancel(); //don't post anything to server
      const text = formData.get("text"); // what does "text" refer to?
      write(text);

      // TODO: reset the form using _____.reset() - what do we want to reset? the element or the data?

      }}>
        <input type="text" id="person">
    </form>

</main>

<style>


section{
    height: 90%;
   
}

form{
    width: 10%;
}

main{
    width: 60vw;
    height: 70vh;
    padding: 10px;
    background-color: rgb(255, 66, 201);
    display: grid;
    grid-template-rows: 90% 10%;
    grid-template-columns: 1fr;
    overflow-y: scroll;
    border-radius: 10px;
    border-color: rgb(219, 12, 194);
}

#visible{
    width: 100px;
    height: 60px;
    display: none;
}

section article{
    margin: 10px;
    background-color: rgb(228, 1, 191);
    width: 90%;
    border-radius: 3px;
}

</style>