<script setup>
import { ref, reactive } from 'vue';
import { userSearchHistoryStore } from '../store/userHistorySearchHistory.js';

const emit = defineEmits(['formSubmit']);

const searchInput = ref('')
const searchHistory = userSearchHistoryStore();

function handleSubmit(e) {
	e.preventDefault();
	searchHistory.pushToHistory(searchInput.value);
	emit('formSubmit', searchInput.value)
}
function showSearchHistory() {
	alert(`History Search:\n${searchHistory.users.join('\n')}`)
}

const state = reactive({
	btn: 'Search'
})

</script>

<template>
	<form @submit="handleSubmit">
		<input type="text" v-model="searchInput">
		<button type="submit" @click="fetchGithubUser">{{ state.btn }}</button>
		<button type="button" @click="showSearchHistory">History</button>

	</form>
</template>


<style scoped>
input,
button {
	max-width: 20rem;
	padding: .5rem;
}

input {

	width: 100%;
	background-color: #1c1a1d;
	border: 1px solid #e91219;
	border-radius: .25rem;
	color: #e5e5e5;
	margin: 1rem 1rem 1rem 0;
}

button {
	background-color: #f64348;
	border: unset;
	border-radius: .25rem;
	color: #1c1a1d;
	font-size: 1rem;
	font-weight: 700;
	margin-left: 1rem;
	text-transform: uppercase;
}

button:hover {
	cursor: pointer;
	transition: 0.6s;
	background-color: #44155b;
	color: #e5e5e5;
	filter: brightness(0.95);
}
</style>