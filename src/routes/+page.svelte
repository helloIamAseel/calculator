 <svelte:head>
   <title>
      A Calculator
   </title>
 </svelte:head>
<script lang="ts"> 
  
  let equation: string ="";

  function addToEquation(value: string){
     equation += value;
  }


</script>



 <div class=" bg-slate-700 rounded-3xl grid grid-cols-4 gap-2 p-6 pt-7
  shadow-slate-900 shadow-2xl">

    <div class="bg-amber-500 rounded-full col-span-4 h-20
     px-4 pt-5 mb-3 text-white text-4xl font-bold
      shadow-slate-700 shadow-md">
    
      {equation}

    </div>

    <button class="bg-white font-extrabold active:bg-gray-400">
       % </button>
    <button class="bg-white pl-4  active:bg-gray-400"> 
        <!--square root icon-->
        <svg xmlns="http://www.w3.org/2000/svg" width="1.5em" height="1.5em" viewBox="0 0 24 24">
            <path fill="currentColor" d="M15.382 4H22v2h-5.382L9 21.236L5.382 14H2v-2h4.618L9 16.764z"/>
        </svg>    
    </button>
      <button class="bg-white  active:bg-gray-400"> CE </button>
      <button class="bg-blue-500 text-white active:bg-blue-700"> 
       C </button>

      <button class="bg-white active:bg-gray-400"> sin </button>
      <button class="bg-white active:bg-gray-400"> cos </button>
      <button class="bg-white active:bg-gray-400"> tan </button>
      <button on:click={() => addToEquation('^')} class="bg-lime-500 active:bg-lime-700 text-white text-3xl">
        ^ </button>

      <button on:click={() => addToEquation('7')}> 7 </button>
      <button on:click={() => addToEquation('8')}> 8 </button>
      <button on:click={() => addToEquation('9')}> 9 </button>
      <button on:click={() => addToEquation('−')} class="bg-red-500 active:bg-red-700 text-white text-3xl"> 
        − </button>

      <button on:click={() => addToEquation('4')}> 4 </button>
      <button on:click={() => addToEquation('5')}> 5 </button>
      <button on:click={() => addToEquation('6')}> 6 </button>
      <button on:click={() => addToEquation('÷')} class="bg-sky-500 active:bg-sky-700 text-white text-3xl">
         ÷ </button>

      <button on:click={() => addToEquation('1')}> 1 </button>
      <button on:click={() => addToEquation('2')}> 2 </button>
      <button on:click={() => addToEquation('3')}> 3 </button>
      <button on:click={() => addToEquation('×')} class="bg-yellow-500 active:bg-yellow-700 text-white text-3xl">
        × </button>
      

      <button> . </button>
      <button on:click={() => addToEquation('0')}> 0 </button>
      <button class="bg-white active:bg-gray-400"> = </button>
      <button on:click={() => addToEquation('+')} class="bg-green-500 active:bg-green-700 text-white text-3xl">
        + </button>
</div>



 

