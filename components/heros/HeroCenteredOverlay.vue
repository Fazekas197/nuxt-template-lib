<!--
  Component: HeroCenteredOverlay

  Description:
  A fullscreen hero section with a background image, dark overlay,
  centered headline and subheadline, and two call-to-action buttons.
  Ideal for home pages, landing pages, or promotional banners where
  the focus is on branding and conversion.

  Props:
  - img: { src: string, alt: string }
      The background image and alt text. Defaults to a placeholder.
  - tagline: string
      A short line of text above the main title. Defaults to generic filler.
  - title: string
      The main heading text. Large and impactful by default.
  - cta1: { title: string, link: string }
      Primary button with solid style. Default: "Learn More"
  - cta2: { title: string, link: string }
      Secondary button with outline style. Default: "Contact Us"

  Example usage:
  <HeroCenteredOverlay
    :img="{ src: '/hero.jpg', alt: 'Scenic view' }"
    tagline="Welcome to our platform"
    title="Achieve More with Less"
    :cta1="{ title: 'Get Started', link: '/start' }"
    :cta2="{ title: 'Learn More', link: '/about' }"
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
			class="absolute inset-0 flex flex-col items-center justify-center text-center text-white px-4 lg:px-20 gap-6"
		>
			<header>
				<p class="text-lg md:text-2xl font-semibold">{{ tagline }}</p>
				<h1 class="text-4xl md:text-6xl lg:text-8xl 2xl:text-[10rem]">
					{{ title }}
				</h1>
			</header>

			<div class="flex gap-4 lg:gap-9">
				<UButton :to="cta1.link" class="text-lg">{{
					cta1.title
				}}</UButton>
				<UButton :to="cta2.link" variant="outline" class="text-lg">
					{{ cta2.title }}
				</UButton>
			</div>
		</section>
	</main>
</template>

<script setup lang="ts">
	type CTA = {
		title: string;
		link: string;
	};

	const props = withDefaults(
		defineProps<{
			img?: { src: string; alt: string };
			tagline?: string;
			title?: string;
			cta1?: CTA;
			cta2?: CTA;
		}>(),
		{
			img: () => ({
				src: "/placeholder.png",
				alt: "Default background image",
			}),
			tagline: "Lorem ipsum dolor sit amet",
			title: "Praesent vehicula dapibus neque",
			cta1: () => ({
				title: "Learn More",
				link: "/",
			}),
			cta2: () => ({
				title: "Contact Us",
				link: "/",
			}),
		}
	);
</script>
