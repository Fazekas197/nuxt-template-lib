<!--
  Component: HeroLeftOverlay

  Description:
  A fullscreen hero section featuring a background image with a dark overlay,
  left-aligned headline, subheadline, and two call-to-action buttons.
  The layout adapts responsively—content is centered on mobile and aligned left on larger screens.
  This component is ideal for landing pages, marketing headers, or any section requiring bold
  visual storytelling paired with clear calls to action.

  Props:
  - img: { src: string, alt: string }
      Background image and its alt description.
      Defaults to a generic placeholder image.
  - title: string
      Main heading. Large and responsive text, intended to grab attention.
      Default: "Praesent vehicula dapibus neque"
  - tagline: string
      Supporting text shown below the title. Default: "Lorem ipsum dolor sit amet"
  - CTA1: { title: string, link: string }
      Primary call-to-action button. Rendered as a filled button.
      Default: { title: "Learn More", link: "/" }
  - CTA2: { title: string, link: string }
      Secondary call-to-action button. Rendered as an outlined button.
      Default: { title: "Contact Us", link: "/" }

  Example usage:
  <HeroLeftOverlay
    :img="{ src: '/images/hero.jpg', alt: 'Modern building at dusk' }"
    title="Welcome to Our Studio"
    tagline="Creative solutions, elegant results"
    :CTA1="{ title: 'Get Started', link: '/start' }"
    :CTA2="{ title: 'View Portfolio', link: '/portfolio' }"
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
			class="absolute inset-0 items-center text-center lg:items-start lg:text-start flex flex-col justify-center text-white px-4 lg:px-20 gap-6 lg:w-3/5"
		>
			<header class="space-y-2 lg:space-y-4">
				<h1 class="text-4xl md:text-6xl xl:text-8xl">
					{{ title }}
				</h1>
				<p class="text-lg md:text-3xl xl:text-4xl font-semibold">
					{{ tagline }}
				</p>
			</header>

			<div class="space-x-4 lg:space-x-5">
				<UButton :to="CTA1.link" class="text-lg lg:text-xl">{{
					CTA1.title
				}}</UButton>
				<UButton
					:to="CTA2.link"
					variant="outline"
					class="text-lg lg:text-xl"
				>
					{{ CTA2.title }}
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
			CTA1?: CTA;
			CTA2?: CTA;
		}>(),
		{
			img: () => ({
				src: "/placeholder.png",
				alt: "Default background image",
			}),
			tagline: "Lorem ipsum dolor sit amet",
			title: "Praesent vehicula dapibus neque",
			CTA1: () => ({
				title: "Learn More",
				link: "/",
			}),
			CTA2: () => ({
				title: "Contact Us",
				link: "/",
			}),
		}
	);
</script>
