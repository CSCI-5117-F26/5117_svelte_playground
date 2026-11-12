<script>
    import counter from "./counter.svelte"
    let name = $state('');
    let facts = $state('');

    async function fetch_new_fact(){
        try{
            const result = await fetch("https://catfact.ninja/fact")
            if (result.ok){
                const data = await result.json()
                facts.push(data.fact)
            } else {
                alert("Fail")
            }
        } catch {
            alert("Failed More")
        } 
    }
</script>

<h1>Welcome, Nimisha, to SvelteKit</h1>
<p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p>

<label for="name-input">Your Name:</label>

<input 
  id="name-input" 
  type="text" 
  bind:value={name} 
  placeholder="Enter your name" 
/>

<ul>
    {#each facts as fact}
        <li>{fact}</li>
    {/each}

</ul>
<button on:click={fetch_new_fact}>Add Fact</button>