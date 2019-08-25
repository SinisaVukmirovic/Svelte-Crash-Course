<script>
    // Event handlers

    let bro = 'Bro';

    function clickEvent() {
        bro = 'Dude';
    }
    
    // ==================================

    // Binding

    let name = 'Svelte';

    // ==================================

    // State/status (checked or not)

    let status = false;

    // ==================================

    // Stores
    // variables should be centralized and stored in one place,
    // not in component level

    import { buddy } from '../stores.js';

    let myFriend;

    const friend = buddy.subscribe(value => {
        myFriend = value;
    });

    function friendChange() {
        buddy.update(name => name = 'Dudde');
    }

    // !!! IMPORTANT !!!
    // Its very important to unsubscribe from the things that we subscribed,
    // to avoid memory leaks!
    import { onDestroy } from 'svelte';

    onDestroy(friend);

    // ======================================

    // Fetching data from an API

    import { onMount } from 'svelte';

    let data = [];
    let i = 1;

    onMount(async function() {
        const apiUrl = 'https://jsonplaceholder.typicode.com/users';

        const response = await fetch(apiUrl);

        data = await response.json();

        console.log(data);
    });

</script>

<style>
    button {
        background-color: lightblue;
        font-weight: bold;
        cursor: pointer;
    }

    h3, em {
        color: lightblue;
    }

    input[type="checkbox"] {
        width: 1.25rem;
        height: 1.25rem;
    }
</style>

<!-- Mark Up -->
<h1>I'm Home</h1>

<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Velit sunt nostrum culpa aliquid nihil a obcaecati, odio hic! Beatae qui eligendi eaque, neque, adipisci quam nisi, porro officia expedita deserunt aperiam. Illum minima ullam ab non numquam? Placeat expedita libero et mollitia aut exercitationem accusantium, vero repellat veritatis illum. Sint.</p>

<hr>

<h1>{bro}</h1>

<button on:click={clickEvent}>Click Me</button>

<hr>

<h3>Describe Svelte.js</h3>
<input bind:value={name}>
<h1>{name}</h1>

<hr>

<label>
    Do you want to learn more Svelte?
    <input type="checkbox" bind:checked={status}>
</label>

{#if status}
    <p>Of course I do!</p>
{:else}
    <p>Nah, I'm gonna stay noob.</p>
{/if}

<hr>

<h1 on:mouseover={friendChange}>Hey <em>{myFriend}</em>, you are comming from stores.js!</h1>
<p>Hover over above sentence to change friend name!</p>

<hr>

<ul>
    {#each data as { address, company, email, name, phone }, i}
        <li>
            <h3>User #{i + 1}:</h3>
            <p><strong>City:</strong> {address.city}</p>
            <p><strong>Company:</strong> {company.name}</p>
            <p><strong>Email:</strong> {email}</p>
            <p><strong>Name:</strong> {name}</p>
            <p><strong>Phone:</strong> {phone}</p>
        </li>
        <hr>
    {/each}
</ul>