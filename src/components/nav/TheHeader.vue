<template>
	<header>
		<h1>
			<router-link to="/">Vue Store</router-link>
		</h1>
		<nav>
			<ul>
				<li>
					<router-link to="/products">Products</router-link>
				</li>
				<li class="middle-part">
					<router-link to="/cart">Cart</router-link>
					<base-badge mode="elegant">{{ getCart.qty }}</base-badge>
				</li>
				<li v-if="getAuth">
					<router-link to="/admin">Admin</router-link>
				</li>
			</ul>
		</nav>
		<div>
			<button v-if="!getAuth" @click="logIn">Login</button>
			<button v-if="getAuth" @click="logOut">Logout</button>
		</div>
	</header>
</template>

<script>
	import { mapGetters, mapActions } from "vuex";

	export default {
		computed: {
			...mapGetters(["getAuth", "getCart"]),
		},

		methods: {
			...mapActions(["logIn", "logOut"]),
		},
	};
</script>

<style scoped>
	header {
		height: 5rem;
		background-color: white;
		margin: 0 10%;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	ul {
		list-style: none;
		margin: 0;
		padding: 0;
		display: flex;
		justify-self: center;
		align-items: center;
	}

	li {
		margin: 0 1rem;
	}

	a {
		text-decoration: none;
		color: #333;
		font-weight: bold;
		border-bottom: 2px solid transparent;
		padding-bottom: 0.25rem;
	}

	a:hover,
	a:active,
	a.router-link-active {
		color: dodgerblue;
		border-color: dodgerblue;
		transition: 0.3s;
	}

	button {
		font: inherit;
		cursor: pointer;
		padding: 0.5rem 1.5rem;
		border: 1px solid dodgerblue;
		background-color: transparent;
		color: dodgerblue;
		border-radius: 30px;
		transition: 0.3s;
	}

	button:hover,
	button:active {
		background-color: rgba(30, 143, 255, 0.1);
	}

	@media screen and (max-width: 500px) {
		header {
			margin: 0 15px;
		}

		h1 {
			font-size: 1.15rem;
		}

		ul {
			gap: 12.5px;
		}

		li {
			font-size: 0.75rem;
			margin: 0;
		}
	}
</style>
