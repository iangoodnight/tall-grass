<script>
  async function fetchMonsters(filter) {
    const host = 'https://www.dnd5eapi.co/api'
    const target = '/monsters'
    const url = `${host}${target}`;
    const result = await fetch(url);
    const json = await result.json();
    const { results } = json;
    return results;
  }

  let monsters = fetchMonsters();

</script>

{#await monsters}
  <p>...Loading monsters</p>
{:then horde}
<ul>
  {#each horde as monster}
    <li>{monster.name}</li>
  {/each}
</ul>
{:catch error}
  <p>Something went wrong</p>
{/await}

<style>

  ul {
    text-align: left;
  }

</style>
