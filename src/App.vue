<template>
	<main>
		<user-list :users="activeUsers" @list-projects="selectUser"></user-list>
		<projects-list :user="selectedUser"></projects-list>
	</main>
</template>

<script>
import { ref } from 'vue';
import USER_DATA from './user-data.js';
import UserList from './components/users/UserList.vue';
import ProjectsList from './components/projects/ProjectsList.vue';

export default {
	components: {
		UserList,
		ProjectsList,
	},
	setup() {
		const selectedUser = ref(null);
		const activeUsers = USER_DATA;

		function selectUser(uid) {
			selectedUser.value = activeUsers.find((usr) => usr.id === uid);
		}

		return { selectUser, selectedUser, activeUsers };
	},
};
</script>

<style>
* {
	box-sizing: border-box;
}
html {
	font-family: sans-serif;
}
body {
	margin: 0;
}

main {
	display: flex;
	justify-content: space-around;
}

button {
	font: inherit;
	outline: none;
	border-radius: 5px;
	border: 1px solid #0040a0;
	background-color: transparent;
	color: #0040a0;
	padding: 0.5rem 1.5rem;
	cursor: pointer;
	margin: 0.5rem 0.5rem 0.5rem 0;
	transition: 100ms ease-in-out;
}
button:hover,
button:active {
	background-color: #eff5ff;
}

button.selected {
	background-color: #0040a0;
	color: white;
}
</style>