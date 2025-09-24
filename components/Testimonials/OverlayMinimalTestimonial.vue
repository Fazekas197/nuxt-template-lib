<!--
  Component: OverlayMinimalTestimonial

  Description:
  A full-width overlay testimonial section with a background image, 
  centered testimonial carousel, and semi-transparent dark overlay. 
  Ideal for landing pages, hero sections, or any section showcasing 
  client feedback.

  Props:
  - img: { src: string; alt: string }
      Background image object containing:
      - src: URL of the background image. Defaults to "/placeholder.png".
      - alt: Alternative text for the image. Defaults to "Default background image".

  - testimonials: string[]
      Array of testimonial texts to display in a carousel.
      Defaults to three placeholder testimonials:
        [
          "Praesent vehicula dapibus neque dolor sit amet",
          "Praesent vehicula dapibus neque dolor sit amet",
          "Praesent vehicula dapibus neque dolor sit amet"
        ]

  Example usage:
  <OverlayMinimalTestimonial
    :img="{ src: '/images/client-bg.webp', alt: 'Clients background' }"
    :testimonials="[
      'Serviciu excelent, recomand cu încredere!',
      'Experiență profesională și plăcută.',
      'Recomand tuturor, comunicare și suport impecabil.'
    ]"
  />
-->

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
