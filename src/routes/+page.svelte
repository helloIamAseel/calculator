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

      let output = document.getElementById('output');
        output?.classList.add('bg-red-500')
       setTimeout(() => {output?.classList.remove('bg-red-500');
       }, 1000);

      clearErrorMessage();

      
       
     }
  }

      function clearErrorMessage(){
        setTimeout(() => {equation = "";} , 1000);
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
     onMount(() => {
       let allButtons = document.getElementsByTagName('button');
       
       for (let i = 0; i < allButtons.length; i++){
          allButtons[i].addEventListener('click', () => {
            new Audio('/click.wav').play();
          })
       }

     });
     
     function onKeyDown(e: KeyboardEvent) {
        let button = document.getElementById(e.key);
        button?.click();
        button?.focus();
        setTimeout(() => {
            // @ts-ignore
            document.activeElement?.blur();
        }, 100);

       
     }
     


</script>

  <svelte:window on:keydown|preventDefault={onKeyDown} />



 <div class=" bg-slate-700 rounded-3xl grid grid-cols-4 gap-2 p-6 pt-7
  shadow-slate-900 shadow-2xl min-h-[35rem] max-w-[90dvm]">

    <div id="output" class="bg-amber-500 rounded-2xl col-span-4 min-h-20 flex items-center px-4  mb-3 text-white text-4xl font-bold
      shadow-slate-700 shadow-md break-all transition-all">
    
      {equation}
      

    </div>

    <button id="%" on:click={() => addToEquation('%')} class="bg-white font-extrabold active:bg-gray-400">
       % </button>
    <button id="sr" on:click={() => addToEquation('sqrt(')} class="bg-white pl-4  active:bg-gray-400"> 
        <!--square root icon-->
        <SquareRoot/>
   </button>
      <button id="Backspace" on:click={backspace} class="bg-white  active:bg-gray-400 pl-1"> <!--backspace icon-->
        <Backspace/>
    </button>
      <button id="C" on:click={clear} class="bg-blue-500 text-white active:bg-blue-700"> 
       C </button>

      <button id="sin" on:click={() => addToEquation('sin(')}
         class="bg-white active:bg-gray-400"> sin </button>
      <button id="cos" on:click={() => addToEquation('cos(')} 
        class="bg-white active:bg-gray-400"> cos </button>
      <button id="tan" on:click={() => addToEquation('tan(')} 
        class="bg-white active:bg-gray-400"> tan </button>
      <button id="^" on:click={() => addToEquation('^')} 
        class="bg-lime-500 active:bg-lime-700 text-white text-3xl">
        ^ </button>

      <button id="7" on:click={() => addToEquation('7')}> 7 </button>
      <button id="8" on:click={() => addToEquation('8')}> 8 </button>
      <button id="9" on:click={() => addToEquation('9')}> 9 </button>
      <button id="-" on:click={() => addToEquation('−')} class="bg-red-500 active:bg-red-700 text-white text-3xl"> 
        − </button>

      <button id="4" on:click={() => addToEquation('4')}> 4 </button>
      <button id="5" on:click={() => addToEquation('5')}> 5 </button>
      <button id="6" on:click={() => addToEquation('6')}> 6 </button>
      <button id="/" on:click={() => addToEquation('÷')} class="bg-sky-500 active:bg-sky-700 text-white text-3xl">
         ÷ </button>

      <button id="1" on:click={() => addToEquation('1')}> 1 </button>
      <button id="2" on:click={() => addToEquation('2')}> 2 </button>
      <button id="3" on:click={() => addToEquation('3')}> 3 </button>
      <button id="*" on:click={() => addToEquation('×')} class="bg-yellow-500 active:bg-yellow-700 text-white text-3xl">
        × </button>
      

      <button id="." on:click={() => addToEquation('.')}> . </button>
      <button id="0" on:click={() => addToEquation('0')}> 0 </button>
      <button id="=" on:click={answer} class="bg-white active:bg-gray-400"> = </button>
      <button id="+" on:click={() => addToEquation('+')} class="bg-green-500 active:bg-green-700 text-white text-3xl">
        + </button>
</div>



 

