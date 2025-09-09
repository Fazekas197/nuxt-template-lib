<!--
  Component: SmallHeroOverlay

  Description:
  A responsive hero banner with a background image and a dark overlay.
  Includes a large heading and a short descriptive paragraph positioned near the bottom.
  Ideal for landing pages, promotional sections, or intros that require bold visuals
  and concise messaging.

  Props:
  - img: { src: string; alt: string }
      Object containing the image source and alternative text.
      Used as the full-width background. Defaults to a placeholder image.
  - title: string
      The main heading text displayed prominently over the image.
      Defaults to "Praesent".
  - text: string
      Supporting paragraph text beneath the title. Useful for brief descriptions
      or slogans. Defaults to placeholder content.

  Example usage:
  <SmallHeroOverlay
    :img="{ src: '/images/hero.jpg', alt: 'Imagine panoramică' }"
    title="Bine ați venit"
    text="Descoperiți colecția noastră de produse premium, create cu grijă pentru fiecare detaliu."
  />
-->

<template>
	<main
		class="relative group w-full bg-cover bg-bottom h-[80vh] flex items-end"
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
		<div
			class="relative px-6 lg:px-[120px] 2xl:px-60 pb-[120px] space-y-6 text-white"
		>
			<TypographyHeroTitleV2>{{ title }}</TypographyHeroTitleV2>
			<TypographyTextBase class="font-semibold leading-snug w-2/5">{{
				text
			}}</TypographyTextBase>
		</div>
	</main>
</template>

<script setup lang="ts">
	import { TypographyHeroTitleV2 } from "#components";

	const props = withDefaults(
		defineProps<{
			img?: { src: string; alt: string };
			title?: string;
			text?: string;
		}>(),
		{
			img: () => ({
				src: "/placeholder.png",
				alt: "Default background image",
			}),
			title: "Praesent",
			text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus varius tincidunt dolor, in venenatis purus dignissim nec. Vestibulum interdum, justo eget iaculis placerat, velit sapien ornare nisi, posuere gravida felis risus a dui.",
		}
	);
</script>
