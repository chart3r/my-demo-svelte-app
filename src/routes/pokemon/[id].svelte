<script context="module">
  export async function load({ page }) {
    const id = page.params.id;
    const url = `https://pokeapi.co/api/v2/pokemon/${id}`;
    const res = await fetch(url);
    const pokeman = await res.json();
    return { props: { pokeman } };
  }
</script>

<script>
  export let pokeman;
  const types = pokeman.types.map((a) => a.type.name);
  const type = types.join(" ");
  let stats = pokeman.stats;
  let statTypes = ["HP", "Attack", "Defence", "SP.Att", "SP.Def", "Speed"];
  let color = ["red","orange","yellow","green","blue","purple"]
</script>

<h1 class="text-4xl text-left my-8 uppercase">{pokeman.name}</h1>
<p>
  Type: <strong>{type}</strong> | Height: <strong>{pokeman.height}</strong> |
  Weight: <strong>{pokeman.weight}</strong>
</p>
<img
  class="card-image"
  src={pokeman.sprites["front_default"]}
  alt={pokeman.name}
/>
<table>
  {#each stats as stat, i}
    <tr>
      <td class="text-right">
        {statTypes[i].padStart(7, " ")}:
      </td>
      <td>
        {stat.base_stat}
      </td>
      <td>
        <svg width="400" height="20"
          ><rect
            fill={color[i]}
            width={stat.base_stat * 2}
            height="20"
            rx="10"
          /></svg
        >
      </td>
    </tr>
  {/each}
</table>
