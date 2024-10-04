<script lang="ts">
  export let password:string;
  export let show:boolean = false;
  export let letter:string = ' ';
  export let won;
  let hidden_password:string = '';

  const password_arr:string[] = password.split('');

  function showLetter(lett:string) {
    for (let i = 0; i < password.length; i++) {
      if (password_arr[i] == lett.toLowerCase()) {
        
        let temp = hidden_password;

        let first_part:string = temp.substring(0, i);
        let last_part:string = temp.substring(i + 1);

        hidden_password = first_part + password_arr[i] + last_part;
      }
    }

    if(hidden_password === password && password!='' && password!=null)
      won=true;
  }

  function hidePassword() {
    password?.split('').forEach(el => {
    if(password !== ' ')
      hidden_password += '_';
    });
  }

  hidePassword();
  showLetter(' ');

  $: if(show) {
    show = false;
    showLetter(letter);
  }
</script>

<div>
  <p>{hidden_password}</p>
</div>

<style>
  div {
    display: flex;
    align-items: center;
    justify-content: center;
    /* height: 150%; */
  }
  p {
    font-size: 50px;
    font-weight: 700;
    letter-spacing: 5px;
    padding-bottom: 10px;
  }
</style>