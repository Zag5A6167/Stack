<script lang="ts">
  import Title from "./Title.svelte";

  let stack: number[] = [];
  let inputVal = '';

  let maxStackDefault:number = 10;
  let maxStack:number = maxStackDefault
  let tempMaxStack :number = 10;
  

  function push(){
   if(inputVal.trim() !== "" && stack.length  < maxStack ){
      const num = Number(inputVal.trim());
      if (!isNaN(num)) {
        stack = [...stack, num];
        inputVal = '';
      }
    }
  }

  function pop(){
    if(stack.length > 0 ){
      stack = stack.slice(0,-1);
    }
  }

  function peek(){
    if (stack.length > 0) {
      alert(stack[stack.length - 1]); 
    } 
  
  }

  function clear(){
    stack = []
  }

  function setMaxStack(){
   const parsedSize = parseInt(tempMaxStack.toString(), 10);
    if (!isNaN(parsedSize) && parsedSize > 0) {
      maxStack = parsedSize;
      alert(`Max Stack is ${maxStack} Now`);
      stack = []
    } 
  }

</script>


<main>
  <Title/>
  <div class="stack-container">
    <div class="stack-items">
      {#each stack as item}
      <div class="stack-item">{item}</div>
    {/each}
    </div>
  </div>
  <label for="maxStackInput">Input Max Stack</label>
<input type="number" id="maxStackInput" bind:value={tempMaxStack}  placeholder="Input Max Stack">
<button onclick={setMaxStack}>Set</button>  
  <div class="controls">
    <input type="text" placeholder="Input Number" bind:value={inputVal}>
    <button onclick={push}>Push</button>
    <button onclick={pop}>Pop</button>
    <button onclick={peek}>Peek</button>
    
    
    <button onclick={clear}>Clear</button>
  </div>

  <div class="stack-container">
    </div>

  <div class="peek-info">
    </div>
</main>


<style>
 

  .controls{
    display: flex;
    gap: 2rem;
   
  }

  .stack-items{
    border: black solid 0.1rem;
    flex-direction: column-reverse;
    display: flex;

  
    
  }
  .stack-item{
      border-bottom: rgb(114, 111, 111) solid 1px;
    }
  
</style>