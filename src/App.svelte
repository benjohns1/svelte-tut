<script>
	import Product from "./Product.svelte";
	import Button from "./Button.svelte";
	import Cart from "./Cart.svelte";

	let title = '';
	let price = 0;
	let description = '';

	let products = [];
	let cartItems = [];

	function createProduct() {
		const newProduct = {
			title,
			price,
			description
		};
		products = [...products, newProduct]
	}

	function addToCart(event) {
		const addTitle = event.detail;
		cartItems = [...cartItems, products.find(prod => prod.title === addTitle)];
		console.log(cartItems);
	}
</script>

<style>
	section {
		width: 30rem;
		margin: auto;
	}
	label, input, textarea {
		width: 100%;
	}
</style>

<section>
	<Cart items={cartItems}/>
</section>

<section>
	<div>
		<label for="title">Title</label>
		<input type="text" id="title" bind:value={title}>
	</div>
	<div>
		<label for="pricce">Price</label>
		<input type="number" id="price" bind:value={price}>
	</div>
	<div>
		<label for="description">Description</label>
		<textarea rows="3" id="description" bind:value={description} />
	</div>
	<Button on:click={createProduct}>Create Product</Button>
</section>

{#if products.length === 0}
	<p>No products</p>
	{:else}
	{#each products as product}
		<Product title={product.title} price={product.price} description={product.description} on:addcart={addToCart}/>
	{/each}
{/if}