<script lang="ts">
  export let password:string;
  export let letter:string;
  export let wrongs:number;
  export let won:boolean;

  const letters = "AĄBCĆDEĘFGHIJKLŁMNŃOÓPRSŚTUWYZŹŻ".toUpperCase().split('');
  let data_value:string;

  function guessLetter(target:string) {
    const button = document.querySelector(`#${target}`);
    letter = target;
    console.log(target);

    if(password.includes(target.toLocaleLowerCase()))
      button?.setAttribute('data-value', 'green');
    else 
      button?.setAttribute('data-value', 'red');
  }
</script>

{#if wrongs < 9 && !won}
  <div id="letters-container">
    {#each letters as letter}
      <button id={letter} on:click|once|preventDefault={() => {guessLetter(letter)}} data-value={data_value} >
        {letter}
      </button>
    {/each}
  </div>
{:else if won}
  <div class="end-msg-container">
    <h2>Wygrałeś! Ilość błędów: </h2>
    <h1 style="color:green">{wrongs}</h1>
  </div>
{:else} 
  <div class="end-msg-container">
    <h2>Przegrałeś! Hasłem było: </h2>
    <h1 style="color: red;"><strong>{password}</strong></h1>
  </div>
{/if}

<style>
  #letters-container {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    gap: 7px;
  }

  button {
    all: unset;
    cursor: pointer;
    font-size: 30px;
    text-align: center;
    border: 2px solid #222;
    color: #aaa;
    border-radius: 20px;
    /* margin: 5px; */
    /* padding: 5px; */
    width: 50px;
    height: 50px;
  }

  button:hover, button:active {
    border-color: #aaa;
  }

  button[data-value='green'] {
    border-color: green;
    color: green;
    user-select: none;
  }

  button[data-value='red'] {
    border-color: red;
    color: red;
    user-select: none;
  }
  
  .end-msg-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
  }

  h1 {
    text-align: center;
    font-weight: 900;
    font-size: 40px;
    width: 100%;
  }

  h2 {
    font-size: 30px;
    width: 100%;
    text-align: center;
  }

</style>