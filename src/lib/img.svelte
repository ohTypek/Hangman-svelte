<script lang="ts">
  export let wrongs:number = 0;
  
</script>

{#if wrongs < 9} 
  <img src="img/s{wrongs}.jpg" alt="Liczba skuch: {wrongs}">
{:else}
  <img src="img/s9.jpg" alt="Przegrałeś, liczba skuch: {wrongs} > 8">
{/if}
