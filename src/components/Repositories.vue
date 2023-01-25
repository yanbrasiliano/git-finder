<script setup>
defineProps(['full_name', 'description', 'html_url'])
</script>

<template>
	<article>
		<h3>Name: {{ full_name }}</h3>
		<p>Description: {{ description }}</p>
		<a :href="html_url" target="_blank">Repository</a>
	</article>
</template>

<style scoped>
h3 {
	margin: 1rem auto .25rem;
}
</style>