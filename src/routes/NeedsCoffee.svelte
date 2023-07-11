<script>
  import { createEventDispatcher } from "svelte";

  let nameInput;
  let selectedOption = "";
  let selectSize = "";
  let errorMessage = "";

  // Create the event dispatcher
  const dispatch = createEventDispatcher();

  function buttonHandler() {
    // Dispatch an event with a custom name
    dispatch("coffeeMessage", {
      name: nameInput,
      type: selectedOption,
      size: selectSize,
    });
  }

  function handleButtonClick() {
    if (!nameInput && !selectedOption) {
      alert((errorMessage = "Please enter a value or select an option"));
    } else {
      buttonHandler();
    }
  }
</script>

<input type="text" bind:value={nameInput} placeholder="Enter your name" />

<select bind:value={selectedOption}>
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

<p>Selected option: {selectedOption}</p>
<button on:click={handleButtonClick}>Order Coffee</button>
