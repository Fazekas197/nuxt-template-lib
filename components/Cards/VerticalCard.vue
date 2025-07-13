<!--
  Component: VerticalCard

  Description:
  A vertically stacked card component that features a responsive image, bold title, descriptive paragraph, and a prominent call-to-action button.
  Optimized for display in a grid of items or as a standalone promotional block. Rounded corners, shadows, and responsive width ensure it fits well into modern UI designs.
  Ideal for product highlights, featured services, or marketing callouts.

  Props:
  - img: { src: string, alt: string }
      The image shown at the top of the card. Automatically fills width and has rounded top corners.
      Default: { src: "/placeholder.png", alt: "Default background image" }

  - title: string
      The main heading displayed below the image. Center-aligned and styled for emphasis.
      Default: "Lorem ipsum"

  - text: string
      Descriptive paragraph content. Displayed under the title with spacing for readability.
      Default: A placeholder lorem ipsum paragraph.

  - cta: { title: string, link: string }
      The call-to-action button displayed at the bottom of the card. Full-width and prominent.
      Default: { title: "Descoperă", link: "/" }

  Example usage:
  <VerticalCard
    :img="{ src: '/images/service.jpg', alt: 'Premium Service' }"
    title="Premium Consulting"
    text="Tailored consulting services to help your business scale effectively and sustainably."
    :cta="{ title: 'Get Started', link: '/services' }"
  />
-->

<template>
	<div
		class="w-full max-w-sm sm:max-w-md md:max-w-lg lg:max-w-xl xl:max-w-[20%] bg-white shadow-2xl rounded-3xl flex flex-col overflow-hidden h-full"
	>
		<NuxtImg
			:src="img.src"
			:alt="img.alt"
			class="w-full h-48 object-cover"
		/>

		<div class="flex flex-col flex-1 px-4 py-5 space-y-4">
			<h4 class="text-3xl text-center">{{ title }}</h4>
			<p class="text-lg flex-1">{{ text }}</p>

			<!-- Button pinned to the bottom -->
			<UButton
				v-if="cta"
				:to="cta.link"
				class="w-full justify-center mt-auto"
			>
				{{ cta.title }}
			</UButton>
		</div>
	</div>
</template>

<script lang="ts" setup>
	type CTA = {
		title: string;
		link: string;
	};

	const props = withDefaults(
		defineProps<{
			img?: { src: string; alt: string };
			title?: string;
			text?: string;
			cta?: CTA;
		}>(),
		{
			img: () => ({
				src: "/placeholder.png",
				alt: "Default background image",
			}),
			title: "Lorem ipsum",
			text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec condimentum a justo in porta. Aenean pretium placerat neque at condimentum. Praesent pharetra libero sit amet condimentum luctus. Cras at erat a erat cursus mollis ac eget arcu. Aenean quis auctor neque. Pellentesque rutrum augue et diam lacinia faucibus luctus sed lacus. Sed lobortis a eros vel interdum. Integer faucibus at erat id rhoncus. Donec luctus felis nec sapien hendrerit dignissim.",
			cta: () => ({
				title: "Descoperă",
				link: "/",
			}),
		}
	);
</script>
