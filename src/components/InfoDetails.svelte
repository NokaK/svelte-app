<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let firstName;
  export let lastName;
  let valid = true;

  $: fullName = firstName + " " + lastName;
  const handleSubmit = () => {
    valid = true;
    if (firstName.trim().length < 3) {
      valid = false;
    }
    if (lastName.trim().length < 5) {
      valid = false;
    }
    if (valid) {
      dispatch("user", fullName);
      firstName = "";
      lastName = "";
    }
  };
</script>

<form class="d-flex flex-column" on:submit|preventDefault={handleSubmit}>
  <slot name="firstName" />
  <input type="text" bind:value={firstName} class:error={!valid} />
  <slot name="lastName" />
  <input type="text" bind:value={lastName} class:error={!valid} />
  <button>Add</button>
</form>

<style>
  input {
    border-radius: 15px;
    padding: 10px 15px;
    margin: 10px 0 0;
    border: 3px solid transparent
  }
  input:focus {
    outline: none;
  }
  button {
    background-color: #496768;
    border-radius: 15px;
    border: none;
    padding: 10px 15px;
    color: #fff;
    box-sizing: border-box;
    transition: all 0.3s linear 0.3s;
    cursor: pointer;
    margin: 15px 0;
    font-weight: bold;
   
  }
  button:hover {
    background-color: #273c3d;
  }
  .error {
    border-color: crimson;
    border-width: 3px;
  }
</style>
