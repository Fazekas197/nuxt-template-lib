<!--
  Component: PromotionBanner

  Description:
  A responsive hero banner with a full-screen background image, dark overlay, 
  and centered text. It displays a large title and a short promotional message, 
  ideal for introductory sections, product highlights, or announcements 
  on landing pages.

  Props:
  - img: { src: string; alt: string }
      An object containing the image URL and its alt text.
      This image is used as the banner background.
      Defaults to a generic placeholder.

  - title: string
      Main headline text that appears prominently over the image.
      Defaults to "Lorem Ipsum".

  - promotion: string
      A supporting line of text below the title.
      Useful for taglines or promotional blurbs.
      Defaults to: "Praesent vehicula dapibus neque dolor sit amet".

  Example usage:
  <PromotionBanner
    :img="{ src: '/images/hero.jpg', alt: 'Imagine panoramică cu munți' }"
    title="Vacanță în inima naturii"
    promotion="Relaxați-vă și bucurați-vă de peisaje uimitoare"
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
			<TypographySectionTitle>{{ title }}</TypographySectionTitle>
			<TypographyTextXl>{{ promotion }}</TypographyTextXl>
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
			title: "Lorem Ipsum",
		}
	);
</script>
