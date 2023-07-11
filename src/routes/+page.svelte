<script>
	import NeedsCoffee from './NeedsCoffee.svelte';
	import OrderResult from './OrderResult.svelte';

	let order = '';

	function handleCoffee(event) {
		order = event.detail.name + " ordered a " + event.detail.size + ' ' + event.detail.type;
	}
	
</script>

<NeedsCoffee on:coffeeMessage={handleCoffee}/>
<OrderResult order={order}/>
