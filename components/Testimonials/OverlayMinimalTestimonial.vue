<template>
	<main
		class="relative group w-full bg-cover bg-bottom h-[60vh] flex items-end"
	>
		<!-- Background -->
		<NuxtImg
			format="webp"
			:src="img.src"
			:alt="img.alt"
			class="absolute inset-0 h-full w-full object-cover"
		/>
		<div class="absolute inset-0 bg-black/35" />

		<!-- Overlay Content -->
		<section
			class="absolute inset-0 flex flex-col items-center justify-center text-center text-white space-y-8 px-8 lg:px-32"
		>
			<TypographySectionTitle>Părerile clienților</TypographySectionTitle>

			<UCarousel
				v-slot="{ item }"
				dots
				:items="testimonials"
				class="w-full mx-auto space-y-8"
			>
				<TypographySubTitle class="!italic">{{
					item
				}}</TypographySubTitle>
			</UCarousel>
		</section>
	</main>
</template>

<script setup lang="ts">
	const props = withDefaults(
		defineProps<{
			img?: { src: string; alt: string };
			testimonials?: string[];
		}>(),
		{
			img: () => ({
				src: "/placeholder.png",
				alt: "Default background image",
			}),
			testimonials: () => [
				"Praesent vehicula dapibus neque dolor sit amet",
				"Praesent vehicula dapibus neque dolor sit amet",
				"Praesent vehicula dapibus neque dolor sit amet",
			],
		}
	);
</script>
