<script>
  import RA from '$lib/assets/NTS/SL-A.jpg?url';
	import { goto } from "$app/navigation";
  import { onMount } from 'svelte';
  import { base } from "$app/paths";
$:{
  let hasItem;
  let valueCheck;
onMount(async () => {
  hasItem = localStorage.getItem('letterKey') !== null;
  valueCheck = localStorage.getItem('letterKey')
  // Conditional logic based on hasItem
  if (hasItem && valueCheck == 'SL-24') 
  {
    
  } 
  else
  {
   goto(base + "/");
  }
});
  }
</script>
  
<div class="text-center m-5">Welcome, Mrs. Rosal, A.</div>
<div class="cheatline text-center">
  Letter finished: June XX, 2024
 </div>
 <header class="overflow-hidden mb-5 flex justify-center">
   <img src={RA} alt="N/A" class="object-cover mt-10 h-[270px] w-[450px] rounded-lg"/>
 </header>
 <h1 class="text-center">*insert final letter here</h1>
<style lang="postcss">
   .cheatline
  {
    background-color: #6D28D9;
    color:#f5f3f3;
  }
  :global(html) {
      background-color: theme(colors.bgPurp);
      color: #dddddd;
    }
</style>