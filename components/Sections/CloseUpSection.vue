<!--
  Component: CloseUpSection

  Description:
  A responsive content section that pairs an image with a title, paragraph text, and optional slot content.
  On larger screens, the layout displays the image on the left and text on the right, with ample spacing.
  On smaller screens, the layout stacks vertically with consistent padding and spacing.
  Ideal for "About Us", feature highlights, or editorial-style content blocks.

  Props:
  - img: { src: string, alt: string }
      The image shown on the left side (or top on mobile). Responsive and set to cover its container.
      Default: { src: "/placeholder.png", alt: "Default background image" }

  - title: string
      The main heading for the section. Responsive size: 5xl on mobile, 6xl on large screens.
      Default: "Lorem ipsum"

  - text: string
      Paragraph text shown below the title. Intended for descriptive or editorial content.
      Responsive size and spacing for improved readability.
      Default: A placeholder lorem ipsum paragraph.

  Slots:
  - default
      Optional slot content that appears below the paragraph, such as buttons or links.

  Example usage:
  <CloseUpSection
    :img="{ src: '/images/team.jpg', alt: 'Our team at work' }"
    title="Meet Our Experts"
    text="Our team brings decades of experience in architecture and design. We believe in creating thoughtful, lasting spaces."
  >
    <NuxtLink to="/about" class="btn btn-primary">Learn More</NuxtLink>
  </CloseUpSection>
-->

<template>
	<section
		class="px-6 py-8 space-y-6 lg:flex lg:gap-x-10 lg:justify-center lg:px-60 lg:py-16 2xl:w-3/4 mx-auto"
	>
		<NuxtImg
			:src="img.src"
			:alt="img.alt"
			format="webp"
			class="lg:w-1/2 object-cover"
		/>

		<div class="space-y-4 lg:w-1/2">
			<h2 ref="textRef" class="mb-5 lg:text-6xl text-5xl leading-none">
				{{ title }}
			</h2>
			<p class="lg:text-lg text-base leading-snug">
				{{ text }}
			</p>
			<slot />
		</div>
	</section>
</template>

<script lang="ts" setup>
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
			title: "Lorem ipsum",
			text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec condimentum a justo in porta. Aenean pretium placerat neque at condimentum. Praesent pharetra libero sit amet condimentum luctus. Cras at erat a erat cursus mollis ac eget arcu. Aenean quis auctor neque. Pellentesque rutrum augue et diam lacinia faucibus luctus sed lacus. Sed lobortis a eros vel interdum. Integer faucibus at erat id rhoncus. Donec luctus felis nec sapien hendrerit dignissim.",
		}
	);
</script>
