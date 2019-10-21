<script>
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";

  let players = [
    {
      name: "John Doe",
      points: 34
    },
    {
      name: "Noah Irwin",
      points: 100
    },
    {
      name: "Arthur Morgan",
      points: 53
    }
  ];

  const addPlayer = event => {
    const newPlayer = event.detail;
    players = [...players, newPlayer];
  };
</script>

<Navbar />
<div class="container">
  <AddPlayer on:addplayer={addPlayer} />
  {#if players.length === 0}
    <p>No players</p>
  {:else}
    {#each players as player}
      <Player name={player.name} points={player.points} />
    {/each}
  {/if}
</div>
