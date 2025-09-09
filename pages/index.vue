<template>
	<div class="space-x-4">
		<NuxtLink to="/heros">Hero Components</NuxtLink>
		<NuxtLink to="/banners">Banner Components</NuxtLink>
		<NuxtLink to="/cards">Cards Components</NuxtLink>
		<NuxtLink to="/sections">Sections Components</NuxtLink>
	</div>

	<div class="overflow-hidden">
		<HeadersClasicHeader />
		<FootersThreeColsFooter />

		<TestimonialsAuthorRatingTestitomial />
	</div>
</template>

<script setup>
	import HeroCenteredOverlay from "~/components/Heros/HeroCenteredOverlay.vue";
</script>
