<script lang="ts">
 interface Teller {
   woord: string,
   aantal: number,
   toets: string,
   visueletoets: string
 }

 function maakTeller(woord: string, toets: string, visueletoets: string): Teller {
   return {
     woord: woord,
     toets: toets,
     aantal: 0,
     visueletoets: visueletoets
   }
 }

 let tellers = [
   maakTeller("hè", "KeyQ", "A"),
   maakTeller("klaar", "KeyW", "Z"),
   maakTeller("oké", "KeyE", "E"),
   maakTeller("in orde", "KeyR", "R"),
   maakTeller("ja", "Space", "spatie"),
 ];


 function incr(i) {
   tellers[i].aantal = tellers[i].aantal + 1;
   tellers = tellers;
 }
function keypress(e) {
   for (let t of tellers) {
     if (e.code == t.toets) {
       t.aantal += 1;
     }
   }

   tellers = tellers;
}
</script>

<svelte:window on:keydown={keypress} />

<main>
  <div class="p-12 bg-violet-200 w-screen h-screen flex flex-col justify-center items-center">
    <h1 class="text-3xl font-bold pb-4">Mariscounter</h1>
    <p class="text-stone-700 pb-8">joa heizoe kinste mekkelijk de weurde van dn Moaris telle eh</p>

    <div class="flex flex-row gap-6">
    {#each tellers as teller, i}
      <div class="flex flex-col p-4 rounded-md shadow-sm bg-violet-300 items-center hover:scale-105 hover:shadow-md transition-all">
        <button on:click={() => incr(i)} class="px-6 py-2 mb-4 bg-violet-500 text-white text-xl font-bold rounded-md
                hover:shadow-lg hover:bg-violet-600 active:bg-violet-900 transition-all">{teller.woord}</button>
        <h2 class="text-2xl text-stone-800 mb-2">{teller.aantal}</h2>
        <kbd>{teller.visueletoets}</kbd>
      </div>
    {/each}
    </div>
  </div>
</main>

<style>
 kbd {
    background-color: #eee;
    border-radius: 3px;
    border: 1px solid #b4b4b4;
    box-shadow: 0 1px 1px rgba(0, 0, 0, 0.2), 0 2px 0 0 rgba(255, 255, 255, 0.7) inset;
    color: #333;
    display: inline-block;
    font-size: 0.85em;
    font-weight: 700;
    line-height: 1;
    padding: 4px 6px;
    white-space: nowrap;
}
</style>
