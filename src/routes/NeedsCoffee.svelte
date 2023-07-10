<script>
    import { createEventDispatcher } from 'svelte';
  
      let nameInput = 'Bob';
      
    // Create the event dispatcher
    const dispatch = createEventDispatcher();
  
      function buttonHandler() {
          // Dispatch an event with a custom name
        dispatch('coffeeMessage', 
                           { 
                                  name: nameInput,
                                  type: 'Capuccino'
                           }
      );
      }
  </script>
  <input type="text" bind:value={nameInput} />
  <button on:click={buttonHandler}>Order Coffee</button>