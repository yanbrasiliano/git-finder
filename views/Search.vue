<script setup>
import Github from '@/components/Github.vue';

</script>

<template>
	<h1>Git Finder &#128269; </h1>

	<Github>
		<template v-slot:footer>
			<footer>
				Developed by <a href="https://github.com/yanbrasiliano" target="_blank" class="foot">
					Yan Brasiliano &#129417;
				</a>
			</footer>
		</template>
	</Github>

</template>

