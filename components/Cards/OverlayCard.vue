<!--
  Component: OverlayCard

  Description:
  A card-style section with a background image, dark overlay,
  and vertically structured content. Includes a headline, description,
  and two call-to-action buttons. Ideal for highlighting featured
  content, promotions, or key offerings within a page layout.

  Props:
  - img: { src: string, alt: string }
      Background image and alt text. Defaults to a placeholder image.
  - title: string
      The main heading displayed at the top. Defaults to "Camere".
  - description: string
      Supporting descriptive text shown below the title.
      Defaults to a vacation-related message.
  - cta1: { title: string, link: string }
      Primary button with solid style. Default: { title: "Learn More", link: "/" }
  - cta2: { title: string, link: string }
      Secondary button with outline style. Default: { title: "Contact Us", link: "/" }

  Example usage:
  <OverlayCard
    :img="{ src: '/room.jpg', alt: 'Mountain cabin room' }"
    title="Elegant Rooms"
    description="Choose from a variety of cozy rooms and enjoy your stay."
    :cta1="{ title: 'View Rooms', link: '/rooms' }"
    :cta2="{ title: 'Book Now', link: '/booking' }"
  />
-->

<template>
	<section
		class="relative rounded-3xl overflow-hidden shadow-2xl lg:w-[624px] lg:h-[465px]"
	>
		<!-- Background -->
		<NuxtImg
			:src="img.src"
			:alt="img.alt"
			format="webp"
			class="absolute inset-0 w-full h-full object-cover"
		/>
		<div class="absolute inset-0 bg-black/35" />

		<!-- Content -->
		<div
			class="relative z-10 flex flex-col justify-between items-center h-full px-8 py-10 text-white space-y-36"
		>
			<!-- Title -->
			<TypographySubTitle class="text-start w-full">{{
				title
			}}</TypographySubTitle>

			<div class="space-y-4">
				<!-- Description -->
				<TypographyTextBase class="text-center">{{
					description
				}}</TypographyTextBase>

				<!-- Buttons -->
				<div class="flex gap-4 justify-center">
					<UButton :to="cta1.link">{{ cta1.title }}</UButton>
					<UButton :to="cta2.link" variant="outline">{{
						cta2.title
					}}</UButton>
				</div>
			</div>
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
			img?: { src: string; alt: string };
			title?: string;
			description?: string;
			cta1?: CTA;
			cta2?: CTA;
		}>(),
		{
			img: () => ({
				src: "/placeholder.png",
				alt: "Default background image",
			}),
			title: "Camere",
			description:
				"De la camere duble și triple, până la întreaga cabană – alege opțiunea perfectă și planifică o vacanță de neuitat!",
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
