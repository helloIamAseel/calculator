 <svelte:head>
   <title>
      A Calculator
   </title>
 </svelte:head>

 <div class=" bg-gray-600 rounded-3xl grid grid-cols-4 gap-2 p-6 pt-7
  shadow-slate-900 shadow-2xl">

    <div class="bg-amber-500 rounded-full col-span-4 h-20
     px-4 pt-5 mb-3 text-white text-4xl font-bold
      shadow-slate-700 shadow-md">
    114

    </div>

      <button class="bg-white font-extrabold"> % </button>
      <button class="bg-white pl-4"> <!--square root icon-->
        <svg xmlns="http://www.w3.org/2000/svg" width="1.5em" height="1.5em" viewBox="0 0 24 24">
            <path fill="currentColor" d="M15.382 4H22v2h-5.382L9 21.236L5.382 14H2v-2h4.618L9 16.764z"/>
        </svg>    
    </button>
      <button class="bg-white"> CE </button>
      <button class="bg-blue-500 text-white"> C </button>

      <button class="bg-white"> sin </button>
      <button class="bg-white"> cos </button>
      <button class="bg-white"> tan </button>
      <button class="bg-lime-500 text-white text-3xl"> ^ </button>

      <button> 7 </button>
      <button> 8 </button>
      <button> 9 </button>
      <button class="bg-red-500 text-white text-3xl"> − </button>

      <button> 4 </button>
      <button> 5 </button>
      <button> 6 </button>
      <button class="bg-sky-500 text-white text-3xl"> ÷ </button>

      <button> 1 </button>
      <button> 2 </button>
      <button> 3 </button>
      <button class="bg-yellow-500 text-white text-3xl"> × </button>
      

      <button> . </button>
      <button> 0 </button>
      <button class="bg-white"> = </button>
      <button class="bg-green-500 text-white text-3xl"> + </button>
</div>



 

