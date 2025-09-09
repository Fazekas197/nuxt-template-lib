<template>
	<div class="space-x-4">
		<NuxtLink to="/heros">Hero Components</NuxtLink>
		<NuxtLink to="/banners">Banner Components</NuxtLink>
	</div>

	<div class="overflow-hidden">
		<HeadersClasicHeader />
		<SectionsCloseUpSection />
		<FootersThreeColsFooter />
		<SectionsFAQSection />
		<CardsVerticalCard />
		<TestimonialsAuthorRatingTestitomial />
		<SectionsGridSection />
		<CardsBlogSummaryCard />
	</div>
</template>

<script setup>
	import HeroCenteredOverlay from "~/components/Heros/HeroCenteredOverlay.vue";
</script>
