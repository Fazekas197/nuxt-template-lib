<!--
  Component: HeroBottomRightOverlay

  Description:
  A fullscreen hero section featuring a background image with a semi-transparent dark overlay,
  and a right-bottom aligned headline. The layout adapts responsively—text is left-aligned on mobile
  and right-aligned on larger screens. Ideal for landing pages or sections where a visually striking
  hero with a simple call-to-action or message is needed.

  Props:
  - img: { src: string, alt: string }
      Background image and its alt description.
      Defaults to a generic placeholder image: { src: "/placeholder.png", alt: "Default background image" }
  - title: string
      Main heading displayed in the bottom-right corner. Large, responsive, and designed to grab attention.
      Default: "Praesent vehicula dapibus neque"

  Example usage:
  <HeroBottomRightOverlay
    :img="{ src: '/images/hero.jpg', alt: 'Sunset over mountains' }"
    title="Explore the World With Us"
  />
-->

<template>
	<main class="relative h-dvh w-dvw">
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
			class="absolute bottom-0 right-0 text-start lg:text-end text-white px-6 py-28 lg:px-16 lg:w-3/5"
		>
			<TypographyHeroTitle>{{ title }}</TypographyHeroTitle>
		</section>
	</main>
</template>

<script setup lang="ts">
	const props = withDefaults(
		defineProps<{
			img?: { src: string; alt: string };
			title?: string;
		}>(),
		{
			img: () => ({
				src: "/placeholder.png",
				alt: "Default background image",
			}),
			title: "Praesent vehicula dapibus neque",
		}
	);
</script>
