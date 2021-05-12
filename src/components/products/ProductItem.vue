<template>
	<li class="product">
		<div class="product__data">
			<div class="product__image">
				<img :src="image" :alt="title" />
			</div>
			<div class="product__text">
				<h3>{{ title }}</h3>
				<base-badge mode="highlight" :no-margin-left="true">
					<h4>₹{{ price }}</h4>
				</base-badge>
				<p>{{ description }}</p>
			</div>
		</div>
		<div class="product__actions">
			<button @click="addToCart">Add to Cart</button>
		</div>
	</li>
</template>

<script>
	import { mapActions } from "vuex";

	export default {
		props: ["id", "image", "title", "price", "description"],
		methods: {
			addToCart() {
				this.addProductToCart({
					productData: {
						id: this.id,
						image: this.image,
						title: this.title,
						price: this.price,
					},
				});
			},

			...mapActions(["addProductToCart"]),
		},
	};
</script>

<style scoped>
	li {
		margin: 1.5rem auto;
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
		padding: 1rem;
		border-radius: 4px;
		transition: 0.3s;
	}

	li:hover {
		transform: translateY(-2px);
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.26);
	}

	.product__data {
		display: flex;
	}

	.product__image {
		margin-right: 1rem;
		border-radius: 4px;
		overflow: hidden;
		height: 10rem;
		width: 10rem;
	}

	.product__image img {
		height: 11rem;
		width: 11rem;
		object-fit: cover;
		display: block;
		transition: 0.3s;
	}

	.product__data:hover .product__image img {
		height: 10rem;
		width: 10rem;
	}

	.product__text h3 {
		margin: 0 0 0.5rem 0;
	}

	.product__text h4 {
		margin: 0;
	}

	.product__actions {
		text-align: center;
	}

	button {
		font: inherit;
		cursor: pointer;
		background-color: rgb(30, 144, 255);
		border: none;
		color: white;
		padding: 0.5rem 1.25rem;
		border-radius: 30px;
		box-shadow: 0 5px 5px rgba(30, 144, 255, 0.25);
		transition: 0.3s;
	}

	button:hover,
	button:active {
		filter: brightness(1.15);
		transform: translateY(-2px);
	}
</style>
