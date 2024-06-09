<script>
  import { base } from "$app/paths";
  
  import CKC from '$lib/assets/TM/KC.jpg?url';
  import CMA from '$lib/assets/TM/MA.jpg?url';
  import MJ from '$lib/assets/TM/J.jpg?url';
  import PE from '$lib/assets/TM/E.jpg?url';
  
  import EK from '$lib/assets/ITCS/KJ.jpg?url';
  import MM from '$lib/assets/ITCS/MK.jpg?url';
  
  import GQ from '$lib/assets/NTS/GA-Q.jpg?url';
  import RA from '$lib/assets/NTS/SL-A.jpg?url';
  import TA from '$lib/assets/NTS/SN-A.jpg?url';
  
  import Modal from './components/Modal.svelte';
  import { goto } from '$app/navigation';
  import {onMount} from 'svelte';
  
  let showModal = false;
  let QKey = "";
  let Question = "";
  let Answer = "";
  $:
  {
    let hasItem;
    onMount(async () => {
    hasItem = localStorage.getItem('letterKey') !== null;
    if (hasItem) 
    {
      localStorage.removeItem('letterKey')
    } 
  });
    // TM
    if (QKey == 'KC')
    {
      Question = import.meta.env.VITE_TM_KC_Q;
      showModal = true;
    }
    else if (QKey == 'MA')
    {
      Question = import.meta.env.VITE_TM_12_Q;
      showModal = true;
    }
    else if (QKey == 'J')
    {
      Question = import.meta.env.VITE_TM_10_Q;
      showModal = true;
    }
    else if (QKey == 'E')
    {
      Question = import.meta.env.VITE_TM_26_Q;
      showModal = true;
    }
    //ITCS 
    else if (QKey == 'KJ')
    {
      Question = import.meta.env.VITE_IT_05_Q;
      showModal = true;
    }
    else if (QKey == 'MK')
    {
      Question = import.meta.env.VITE_CS_15_Q;
      showModal = true;
    }
    //NTS
    else if (QKey == 'Q')
    {
      Question = import.meta.env.VITE_GA_15_Q;
      showModal = true;
    }
    else if (QKey == 'SL-A')
    {
      Question = import.meta.env.VITE_SL_24_Q;
      showModal = true;
    }
    else if (QKey == 'SN-A')
    {
      Question = import.meta.env.VITE_SN_19_Q;
      showModal = true;
    }
  }
   
  const answerCheck = () =>
  {
    //TM
    if (Answer == import.meta.env.VITE_TM_KC_A1 || Answer == import.meta.env.VITE_TM_KC_A2)
    {
      localStorage.setItem('letterKey', 'TM-KC');
      goto(base + "/TM/TM-KC");
    }
    else if (Answer == import.meta.env.VITE_TM_12_A)
    {
      localStorage.setItem('letterKey', 'TM-12');
      goto(base + "/TM/TM-12");
    }
    else if (Answer == import.meta.env.VITE_TM_10_A)
    {
      localStorage.setItem('letterKey', 'TM-10');
      goto(base + "/TM/TM-10");
    }
    else if (Answer == import.meta.env.VITE_TM_26_A)
    {
      localStorage.setItem('letterKey', 'TM-26');
      goto(base + "/TM/TM-26");
    }
    //ITCS
    else if (Answer == import.meta.env.VITE_IT_05_A1 || Answer ==  import.meta.env.VITE_IT_05_A2)
    {
      localStorage.setItem('letterKey', 'IT-05');
      goto(base + "/IT/IT-05");
    }
    else if (Answer == import.meta.env.VITE_CS_15_A)
    {
      localStorage.setItem('letterKey', 'CS-15');
      goto(base + "/CS/CS-15");
    }
    //NTS
    else if (Answer == import.meta.env.VITE_GA_15_A)
    {
      localStorage.setItem('letterKey', 'GA-15');
      goto(base + "/NTS/GA-15");
    }
    else if (Answer == import.meta.env.VITE_SL_24_A1 || Answer == import.meta.env.VITE_SL_24_A2)
    {
      localStorage.setItem('letterKey', 'SL-24');
      goto(base + "/NTS/SL-24");
    }
    else if (Answer == import.meta.env.VITE_SN_19_A)
    { 
      localStorage.setItem('letterKey', 'SN-19');
      goto(base + "/NTS/SN-19");
    }
    Answer = ""
  }
  </script>
  <title>Letter Storage System</title>
  <h1 class="text-3xl text-center m-9 mb-4">
      Welcome
  </h1>
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <!-- svelte-ignore a11y-img-redundant-alt -->
   <h1 class="text-lg m-2 text-center"> Please select your Year/Course or work in the list below </h1>
    <div class="row">
      <!-- TM -->
      <div class="gridName">
        <h1 class="text-2xl mb-2 ml-5">Tourism Management</h1> 
        <img src={CKC} alt="N/A" class="object-cover ml-5 h-[150px] w-[150px] rounded-lg"/>
        <div class="gridDesc flex overflow-hidden mb-5 text-center" on:click={() => QKey = "KC"}> 
          <p class="text-xl ml-5 textRealign">
            3rd year <br/> TM-KC
          </p>
        </div> 
        <div class="gridDesc flex overflow-hidden mb-5" on:click={() => QKey = "MA"}> 
          <img src={CMA} alt="N/A" class="object-cover ml-5 h-[150px] w-[150px] rounded-lg"/>
          <p class="text-xl ml-4">
            1st year <br/> TM-12
          </p>
        </div> 
        <div class="gridDesc flex overflow-hidden mb-5" on:click={() => QKey = "J"}> 
          <img src={MJ} alt="N/A" class="object-cover ml-5 h-[150px] w-[150px] rounded-lg"/>
          <p class="text-xl ml-4">
            1st year <br/> TM-10
          </p>
        </div>
        <div class="gridDesc flex overflow-hidden mb-5" on:click={() => QKey = "E"}> 
          <img src={PE} alt="N/A" class="object-cover ml-5 h-[150px] w-[150px] rounded-lg"/>
          <p class="text-xl ml-4">
            1st year <br/> TM-26
          </p>
        </div>  
      </div>
      <!-- IT/CS -->
      <div class="gridName"> 
        <h1 class="text-2xl mb-2">ICT</h1>
        <div class="gridDesc flex overflow-hidden mb-5" on:click={() => QKey = "KJ"}> 
          <img src={EK} alt="picture niya" class="object-cover h-[150px] w-[150px] rounded-lg"/>
          <p class="text-xl ml-4">
            3rd year | IT <br/> IT-05
          </p>
        </div>
        <div class="gridDesc flex overflow-hidden mb-5" on:click={() => QKey = "MK"}> 
          <img src={MM} alt="picture niya" class="object-cover h-[150px] w-[150px] rounded-lg"/>
          <p class="text-xl ml-4">
            2nd year | CS <br/> CS-15
          </p>
        </div>  
      </div>
      <!-- NTS -->
      <div class="gridName"> 
        <h1 class="text-2xl mb-2">Non-Teaching Staff</h1>
        <div class="gridDesc flex overflow-hidden mb-5" on:click={() => QKey = "Q"}> 
          <img src={GQ} alt="picture niya" class="object-cover h-[150px] w-[150px] rounded-lg"/>
          <p class="text-xl ml-4">
            Guidance Associate <br/> GA-15
          </p>
        </div> 
        <div class="gridDesc flex overflow-hidden mb-5" on:click={() => QKey = "SL-A"}> 
          <img src={RA} alt="picture niya" class="object-cover h-[150px] w-[150px] rounded-lg"/>
          <p class="text-xl ml-4">
            School Librarian <br/> SL-24
          </p>
        </div> 
        <div class="gridDesc flex overflow-hidden mb-5" on:click={() => QKey = "SN-A"}> 
          <img src={TA} alt="picture niya" class="object-cover h-[150px] w-[150px] rounded-lg"/>
          <p class="text-xl ml-4">
            School Nurse <br/> SN-19
          </p>
        </div> 
      </div>
    </div>
  
  <Modal bind:showModal>
    <h2 slot="header" class="text-2xl text-center">
      Passphrase
    </h2>
    <p class="text-base text-center textWarning">USE PROPER CAPITALIZATION</p>
    <p class="text-base text-center">{Question}</p>
    <form on:submit|preventDefault={answerCheck} class="text-center">
      <input type="text" class="border-b-2 rounded-sm m-2" placeholder="Answer" bind:value={Answer}>
      <hr />
      <button class="text-white inline-flex w-full justify-center font-medium text-sm px-5 py-2.5 text-center">Submit</button>
    </form>
  </Modal>
  <style lang="postcss">
      *{
        box-sizing: border-box;
      }
      .textWarning
      {
        color: #991B1B;
      }
      .gridName
      {
        float: left;
        width: 33.33%;
        padding: 10px;
      }
      .gridDesc
      {
        display: grid;
        grid-template-columns: 50% 50%;
        align-items: center;
        cursor: pointer;
      }
      .row:after {
      content: "";
      display: table;
      clear: both;
      }
      @media screen and (max-width: 600px) {
      .gridName  {
      width: 100%;
        }
      }
      :global(html) {
        background-color: theme(colors.bgBlack);
        color: #dddddd;
      }
  </style>