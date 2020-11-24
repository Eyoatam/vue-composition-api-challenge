<template>
	<form>
		<input
			type="search"
			@input="search"
			:value="searchTerm"
			placeholder="Filter items"
		/>
	</form>
</template>

<script>
export default {
	props: ['searchTerm'],
	emits: ['search'],
	setup(props, context) {
		function search(event) {
			context.emit('search', event.target.value);
		}

		return { search };
	},
};
</script>

<style scoped>
input {
	font: inherit;
	width: 100%;
	display: block;
	padding: 0.5rem;
	border: 1px solid #ccc;
	border-radius: 5px;
}

input:focus {
	outline: none;
	border-color: #0061b1;
	background-color: #eef6ff;
}
</style>