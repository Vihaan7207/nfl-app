<script>
    import { onMount } from "svelte";
    import { PUBLIC_API_KEY } from "$env/static/public";

    let standings;
    const date = new Date();
    const year = date.getFullYear();

    let response;

    onMount(async() => {
        try {
            response = await fetch(`https://api.sportsdata.io/v3/nfl/scores/json/Standings/2024?key=${PUBLIC_API_KEY}`);
            standings = await response.json();
        } catch (error) {

        }
    });
</script>

{#if standings}
    <!-- <pre>{JSON.stringify(standings, null, 2)}</pre> -->
{:else}
    <p>Loading standings...</p>
{/if}