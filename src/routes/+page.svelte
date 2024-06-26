 <svelte:head>
   <title>
      A Calculator
   </title>
 </svelte:head>

<script lang="ts"> 
   import { onMount } from 'svelte';
   import { evaluate } from 'mathjs';

  import SquareRoot from "$lib/icons/squareRoot.svelte";
  import Backspace  from "$lib/icons/backspace.svelte";

  let equation: string ="";
  

  function addToEquation(value: string) {
    equation += convertSpecialChars(value);
    
  }

  function backspace() {
    equation = equation.substring(0, equation.length - 1);
    
  }


   function clear(){
   
    equation = "";
   
    
   }
    
   function balanceParentheses(equation: string): string {
    let openParentheses = 0;
    let closeParentheses = 0;

    for (let char of equation) {
      if (char === '(') {
        openParentheses++;
      } else if (char === ')') {
        closeParentheses++;
      }
    }

    while (openParentheses > closeParentheses) {
      equation += ')';
      closeParentheses++;
    }

    return equation;
  }


  function answer() {
    try {
      let balancedEquation = balanceParentheses(equation);
      equation = evaluate(balancedEquation).toString();
      
    } catch (error) {
      equation = "Error";
    }
  }


   // Convert special characters to their math.js equivalents
   function convertSpecialChars(char: string): string {
  switch(char) {
    case '<SquareRoot/>':
      return 'sqrt(';
    case 'sin':
      return 'sin(';
    case 'cos':
      return 'cos(';
    case 'tan':
      return 'tan(';
    case '^':
      return '^';
    case '÷':
      return '/';
    case '×':
      return '*';
    case '−':
      return '-';
    case '+':
      return '+';
    default:
      return char;
    }
  }

</script>



 <div class=" bg-slate-700 rounded-3xl grid grid-cols-4 gap-2 p-6 pt-7
  shadow-slate-900 shadow-2xl min-h-[35rem] w-[25rem]">

    <div class="bg-amber-500 rounded-2xl col-span-4 min-h-20 flex items-center px-4  mb-3 text-white text-4xl font-bold
      shadow-slate-700 shadow-md break-all">
    
      {equation}
      

    </div>

    <button on:click={() => addToEquation('%')} class="bg-white font-extrabold active:bg-gray-400">
       % </button>
    <button on:click={() => addToEquation('sqrt(')} class="bg-white pl-4  active:bg-gray-400"> 
        <!--square root icon-->
        <SquareRoot/>
   </button>
      <button on:click={backspace} class="bg-white  active:bg-gray-400 pl-1"> <!--backspace icon-->
        <Backspace/>
    </button>
      <button on:click={clear} class="bg-blue-500 text-white active:bg-blue-700"> 
       C </button>

      <button on:click={() => addToEquation('sin(')}
         class="bg-white active:bg-gray-400"> sin </button>
      <button on:click={() => addToEquation('cos(')} 
        class="bg-white active:bg-gray-400"> cos </button>
      <button on:click={() => addToEquation('tan(')} 
        class="bg-white active:bg-gray-400"> tan </button>
      <button on:click={() => addToEquation('^')} 
        class="bg-lime-500 active:bg-lime-700 text-white text-3xl">
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
      

      <button on:click={() => addToEquation('.')}> . </button>
      <button on:click={() => addToEquation('0')}> 0 </button>
      <button on:click={answer} class="bg-white active:bg-gray-400"> = </button>
      <button on:click={() => addToEquation('+')} class="bg-green-500 active:bg-green-700 text-white text-3xl">
        + </button>
</div>



 

