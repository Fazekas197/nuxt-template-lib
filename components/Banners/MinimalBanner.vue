<!--
  Component: MinimalBanner

  Description:
  A clean, responsive banner component featuring a full-width background image 
  with a subtle dark overlay and centered promotional text. Ideal for hero 
  sections, simple call-to-action headers, or promotional highlights on 
  landing pages.

  Props:
  - img: { src: string; alt: string }
      An object containing the image URL and its alt text.
      This image is displayed as the banner background.
      Defaults to { src: "/placeholder.png", alt: "Default background image" }.

  - title: string
      (Currently unused in the template, but available for future customization.)
      Main headline text to display over the background.

  - promotion: string
      A supporting tagline or promotional message displayed at the center 
      of the banner.
      Defaults to: "Praesent vehicula dapibus neque dolor sit amet".

  Example usage:
  <MinimalBanner
    :img="{ src: '/images/banner.jpg', alt: 'Beautiful landscape' }"
    promotion="Discover breathtaking destinations"
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
			class="absolute inset-0 flex flex-col items-center justify-center text-center text-white px-12 lg:px-20 gap-3 lg:gap-6"
		>
			<TypographyHeroSubtitle>{{ promotion }}</TypographyHeroSubtitle>
		</section>
	</main>
</template>

<script setup lang="ts">
	const props = withDefaults(
		defineProps<{
			img?: { src: string; alt: string };
			title?: string;
			promotion?: string;
		}>(),
		{
			img: () => ({
				src: "/placeholder.png",
				alt: "Default background image",
			}),
			promotion: "Praesent vehicula dapibus neque dolor sit amet",
		}
	);
</script>
