<script>
  import { createEventDispatcher } from "svelte";

  let nameInput;
  let selectCoffeeType = "";
  let selectSize = "";
  let errorMessage = "";

  // Create the event dispatcher
  const dispatch = createEventDispatcher();

  function buttonClickHandler() {
    
    if(checkEmptyFields()) {
        alert((errorMessage = "Please enter a value or select an option"));
    } else {
        dispatchMessage();
    }
  }

  function dispatchMessage() {
    // Dispatch an event with a custom name
    dispatch("coffeeMessage", {
      name: nameInput,
      type: selectCoffeeType,
      size: selectSize,
    });
  }

  // return true if any fields are empty.  false if none are empty
  function checkEmptyFields() {
    if (!nameInput || !selectCoffeeType || !selectSize) {
      return true;
    } else {
      return false;
    }
  }
</script>

<input type="text" bind:value={nameInput} placeholder="Enter your name" />

<select bind:value={selectCoffeeType}>
  <option value="">Select an option</option>
  <option value="Cappuccino">Cappuccino</option>
  <option value="Latte">Latte</option>
  <option value="Espresso">Espresso</option>
  <option value="Chocolate">Chocolate</option>
</select>

<select bind:value={selectSize}>
  <option value="">Select an option</option>
  <option value="Large">Large</option>
  <option value="Medium">Medium</option>
  <option value="Small">Small</option>
</select>

<p>Selected option: {selectCoffeeType}</p>
<button on:click={buttonClickHandler}>Order Coffee</button>
<style>
  p{
    color:red;
  }
  button{
    color: blue;
  }
</style>