<script setup>
defineProps(['full_name', 'description', 'html_url'])
</script>

<template>
	<article>
		<h3> {{ full_name }}</h3>
		<p> {{ description }}</p>
		<a :href="html_url" target="_blank" >Repository</a>
	</article>
</template>

<style scoped>
a{
	text-decoration: none;
}
a:hover{
	color: #fff;
}
article{
	margin-top: 1rem;
	border: 1px solid #e91219;
	padding: 1rem;
}
article:hover{
	background-color: #3f3e3e; ;
}
h3 {
	margin: 1rem auto .25rem;
}
</style>