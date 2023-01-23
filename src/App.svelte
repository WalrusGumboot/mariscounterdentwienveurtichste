<script lang="ts">
let tellers = ["hè", "klaar", "oké"].map(e => { return {woord: e, aantal: 0} });

function meer_graag(index: number) {
  tellers[index].aantal = tellers[index].aantal + 1;
  tellers = tellers;
}

function keypress(e) {
  switch (e.code) {
      case "KeyQ": meer_graag(0); break;
      case "KeyW": meer_graag(1); break;
      case "KeyE": meer_graag(2); break;
      default: break;
  }
}
</script>

<svelte:window on:keydown={keypress} />

<main>
  <div class="p-12 bg-violet-200 w-screen h-screen flex flex-col justify-center items-center">
    <h1 class="text-3xl font-bold pb-4">Mariscounter</h1>
    <p class="text-stone-700 pb-8">joa heizoe kinste mekkelijk de weurde van dn Moaris telle eh</p>

    <div class="flex flex-row gap-6">
    {#each tellers as teller, i}
      <div class="flex flex-col p-4 rounded-md shadow-sm bg-violet-300 items-center">
        <button on:click={() => meer_graag(i)} class="px-6 py-2 mb-4 bg-violet-500 text-white text-xl font-bold rounded-md
                hover:shadow-lg hover:bg-violet-600 active:bg-violet-900 transition-all">{teller.woord}</button>
        <h2 class="text-2xl text-stone-800">{teller.aantal}</h2>
      </div>
    {/each}
    </div>
  </div>
</main>
