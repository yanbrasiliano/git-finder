<script setup>
import { reactive, computed } from 'vue';
import User from '@/components/User.vue';
import Repositories from '@/components/Repositories.vue';
import Form from '@/components/Form.vue';



const state = reactive({
	login: '',
	name: '',
	bio: '',
	company: '.',
	avatar_url: '',
	repo: [],
	
})

async function fetchGithubUser(username) {
	

	const res = await fetch(`https://api.github.com/users/${username}`)
	const { login, name, bio, company, avatar_url } = await res.json()

	state.login = login
	state.name = name
	state.bio = bio
	state.company = company
	state.avatar_url = avatar_url
	state.btn = 'Search'

	fetchGithubRepositories();

}

async function fetchGithubRepositories() {

	const res = await fetch(`https://api.github.com/users/${state.login}/repos`)
	const repos = await res.json()


	state.repo = repos

}
const reposCountMessage = computed(() => {
	return state.repo.length > 0
		? `${state.name} has ${state.repo.length} public repositories.`
		: `${state.name} don't have any public repositories.`
})
</script>

<template>

	<h1>Git Finder</h1>
	<p> User: {{ state.searchInput }} </p>

	<Form @formSubmit ="fetchGithubUser" v-model="state.searchInput"/>
	<User v-if="state.login !== ''" :login="state.login" :name="state.name" :company="state.company" :bio="state.bio"
		:avatar_url="state.avatar_url" />

	<section v-if="state.repo.length > 0">
		<h2>{{ reposCountMessage }}</h2>
		<article>
			<Repositories v-for="repo of state.repo" :full_name="repo.full_name" :description="repo.description"
				:html_url="repo.html_url" />
		</article>
	</section>

</template>


<style >

a {
	color: #f64348;
}
</style>