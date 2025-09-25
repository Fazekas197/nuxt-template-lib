<!--
  Component: ProductPromoSection

  Description:
  A promotional section component designed to showcase a product or offering with a title, 
  two responsive images, and a call-to-action button. 
  The layout is optimized for both mobile and desktop: stacked vertically on small screens 
  and displayed in a two-column format on larger screens. 
  Ideal for highlighting key products, services, or campaigns in a visually engaging manner.

  Props:
  - img1: { src: string, alt: string }
      The first image displayed in the left column (below the title and CTA on desktop, 
      or stacked on mobile). Styled with `object-cover` for responsive fit.
      Default: { src: "/placeholder.png", alt: "Default background image" }

  - img2: { src: string, alt: string }
      The second image displayed in the right column (or stacked on mobile). 
      Styled with fixed height on mobile (`h-[525px]`) and full height on larger screens.
      Default: { src: "/placeholder.png", alt: "Default background image" }

  - title: string
      The main heading displayed at the top-left section. 
      Typically used for product or campaign names.
      Default: "Miere polifloră, obținută prin metode tradiționale"

  - cta: { title: string, link: string }
      A call-to-action button displayed below the title. 
      On mobile it spans full width, while on desktop it sizes to fit content.
      Default: { title: "Learn More", link: "/" }

  Example usage:
  <ProductPromoSection
    :img1="{ src: '/images/honey-jar.jpg', alt: 'Organic Honey Jar' }"
    :img2="{ src: '/images/beehive.jpg', alt: 'Traditional Beehive' }"
    title="Pure Organic Honey from Traditional Beekeeping"
    :cta="{ title: 'Shop Now', link: '/shop' }"
  />
-->

<template>
	<section
		class="space-y-8 lg:space-y-0 px-8 py-16 lg:flex lg:gap-x-8 lg:px-40 lg:justify-center"
	>
		<div class="space-y-8 lg:w-2/5">
			<TypographySectionTitle>{{ title }}</TypographySectionTitle>
			<UButton :to="cta.link" class="w-full justify-center lg:w-fit">{{
				cta.title
			}}</UButton>
			<NuxtImg
				:src="img1.src"
				:alt="img1.alt"
				format="webp"
				class="object-cover"
			/>
		</div>
		<div class="lg:w-2/5">
			<NuxtImg
				:src="img2.src"
				:alt="img2.alt"
				format="webp"
				class="object-cover h-[525px] lg:h-full"
			/>
		</div>
	</section>
</template>

<script setup lang="ts">
	type CTA = {
		title: string;
		link: string;
	};

	const props = withDefaults(
		defineProps<{
			img1?: { src: string; alt: string };
			img2?: { src: string; alt: string };
			title?: string;
			cta?: CTA;
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
			title: "Miere polifloră, obținută prin metode tradiționale",
			cta: () => ({
				title: "Learn More",
				link: "/",
			}),
		}
	);
</script>
