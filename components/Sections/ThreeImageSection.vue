<!--
  Component: ThreeImageSection

  Description:
  A responsive image section component designed to display three images 
  in a visually balanced layout. 
  The first image spans the full width at the top, while the second and third images 
  are displayed side by side below it. 
  Optimized for both mobile and desktop: stacked layout on smaller screens 
  and a clean, proportional arrangement on larger screens.
  Ideal for showcasing product collections, galleries, or lifestyle imagery.

  Props:
  - img1: { src: string, alt: string }
      The main featured image displayed at the top of the section. 
      Styled with `object-cover` and constrained with `max-h-[732px]` for responsiveness.
      Default: { src: "/placeholder.png", alt: "Default background image" }

  - img2: { src: string, alt: string }
      The first secondary image displayed on the left in the second row 
      (or stacked below the main image on smaller screens). 
      Styled with `object-cover`, flexible sizing, and responsive aspect ratio. 
      Default: { src: "/placeholder.png", alt: "Default background image" }

  - img3: { src: string, alt: string }
      The second secondary image displayed on the right in the second row 
      (or stacked below the first secondary image on smaller screens). 
      Styled similarly to `img2` for balanced layout. 
      Default: { src: "/placeholder.png", alt: "Default background image" }

  Example usage:
  <ThreeImageSection
    :img1="{ src: '/images/hero.jpg', alt: 'Main Showcase Image' }"
    :img2="{ src: '/images/detail-left.jpg', alt: 'Supporting Detail Left' }"
    :img3="{ src: '/images/detail-right.jpg', alt: 'Supporting Detail Right' }"
  />
-->

<template>
	<section class="space-y-4 lg:space-y-6">
		<div>
			<NuxtImg
				:src="img1.src"
				:alt="img1.alt"
				format="webp"
				class="object-cover w-full max-h-[732px]"
			/>
		</div>
		<div class="space-x-4 flex lg:space-x-6">
			<NuxtImg
				:src="img2.src"
				:alt="img2.alt"
				format="webp"
				class="object-cover flex-1 w-full min-w-0 aspect-square lg:aspect-auto lg:max-h-[416px]"
			/>
			<NuxtImg
				:src="img3.src"
				:alt="img3.alt"
				format="webp"
				class="object-cover flex-1 w-full min-w-0 aspect-square lg:aspect-auto lg:max-h-[416px]"
			/>
		</div>
	</section>
</template>

<script setup lang="ts">
	const props = withDefaults(
		defineProps<{
			img1?: { src: string; alt: string };
			img2?: { src: string; alt: string };
			img3?: { src: string; alt: string };
		}>(),
		{
			img1: () => ({
				src: "/placeholder.png",
				alt: "Default background image",
			}),
			img2: () => ({
				src: "/placeholder.png",
				alt: "Default background image",
			}),
			img3: () => ({
				src: "/placeholder.png",
				alt: "Default background image",
			}),
		}
	);
</script>
