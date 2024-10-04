<script lang="ts">
  import Password from "./lib/password.svelte";
  import Img from "./lib/img.svelte";
  import Letters from "./lib/letters.svelte";

  const password:string = prompt('Podaj hasło: ')?.toLowerCase() ?? '';
  let wrongs:number = 0;
  let letter:string = '';
  let show:boolean;
  let won:boolean;

  $: if(!password.includes(letter.toLocaleLowerCase())) {
    wrongs+=1;
    console.log(wrongs);
  } else {
    show = true;
  }

</script>

<main>
  <header>
  <Password {password} bind:letter bind:show bind:won />
  </header>
  <section>
    <Img {wrongs} />
  </section>
  <section>
    <Letters {password} bind:letter bind:wrongs bind:won />
  </section>
</main>