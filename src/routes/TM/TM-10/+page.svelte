<script>
  import MJ from '$lib/assets/TM/J.jpg?url';
	import { goto } from "$app/navigation";
  import { onMount } from 'svelte';
$:{
  let hasItem;
  let valueCheck;
onMount(async () => {
  hasItem = localStorage.getItem('letterKey') !== null;
  valueCheck = localStorage.getItem('letterKey')
  // Conditional logic based on hasItem
  if (hasItem && valueCheck == 'TM-10') 
  {
    
  } 
  else
  {
   goto("/");
  }
});
  }
</script>

<div class="text-center m-5">Welcome, Margate, J.</div>
<div class="cheatline text-center">
  Letter finished: June XX, 2024
 </div>
 <header class="overflow-hidden mb-5 flex justify-center">
   <img src={MJ} alt="N/A" class="object-cover mt-10 h-[250px] w-[450px] rounded-lg"/>
 </header>
 <h1 class="text-center">*insert final letter here</h1>
<style lang="postcss">
    .cheatline
  {
    background-color: #b76e79;
    color:#f5f3f3;
  }
  :global(html) {
      background-color: theme(colors.bgRoseGold);
      color: #dddddd;
    }
</style>