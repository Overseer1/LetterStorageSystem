<script>
  import CMA from '$lib/assets/TM/MA.jpg?url';
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
  if (hasItem && valueCheck == 'TM-12') 
  {
    
  } 
  else
  {
   goto(base +"/");
  }
});
  }
</script>
<div class="text-center m-5">Welcome, Cabrera, M. A.</div>
<div class="cheatline text-center">
  Letter finished: June XX, 2024
 </div>
 <header class="overflow-hidden mb-5 flex justify-center">
   <img src={CMA} alt="N/A" class="object-cover mt-10 h-[250px] w-[450px] rounded-lg"/>
 </header>
 <h1 class="text-center">*insert final letter here</h1>
<style lang="postcss">
     .cheatline
  {
    background-color: #fd5da8;
    color:#f5f3f3;
  }
  :global(html) {
      background-color: theme(colors.bgPink);
      color: #dddddd;
    }
</style>
  