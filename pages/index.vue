<template>
	<div class="space-x-4">
		<NuxtLink to="/heros">Hero Components</NuxtLink>
		<NuxtLink to="/banners">Banner Components</NuxtLink>
		<NuxtLink to="/cards">Cards Components</NuxtLink>
		<NuxtLink to="/sections">Sections Components</NuxtLink>
		<NuxtLink to="/testimonials">Testimonials Components</NuxtLink>
		<NuxtLink to="/headers">Headers Components</NuxtLink>
		<NuxtLink to="/footers">Footers Components</NuxtLink>
	</div>

	<div class="overflow-hidden">
		<HeadersClasicHeader />
		<HerosHeroCenteredOverlay />
		<HerosHeroLeftOverlay />
		<HerosSmallHeroOverlay />
		<HerosHeroBottomRightOverlay />
		<SectionsCloseUpSection />
		<FootersThreeColsFooter />
		<SectionsFAQSection />
		<CardsVerticalCard />
		<BannersPromotionBanner />
		<TestimonialsAuthorRatingTestitomial />
		<SectionsGridSection />
		<CardsBlogSummaryCard />
	</div>
</template>
