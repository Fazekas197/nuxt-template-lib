<!--
  Component: HalfImageSection

  Description:
  A responsive two-column section with an image on the left (desktop) 
  and flexible content on the right. Designed for storytelling sections, 
  about pages, or feature highlights. On smaller screens, the image 
  stacks above the content.

  Props:
  - img: { src: string; alt: string }
      Image object for the left side of the section.
      - src: URL of the image. Defaults to "/placeholder.png".
      - alt: Alternative text for the image. Defaults to "Default background image".

  Slots:
  - default
      The main content area on the right side.
      You can insert any elements such as titles, paragraphs, buttons, 
      or other components. By default, it includes:
        <TypographySectionTitle>Povestea Noastră</TypographySectionTitle>
        <TypographyTextBase> ... </TypographyTextBase>
        <UButton>Citește mai mult</UButton>

  Example usage:
  <HalfImageSection
    :img="{ src: '/images/about-us.webp', alt: 'Our team working' }"
  >
    <TypographySectionTitle>Despre Noi</TypographySectionTitle>
    <TypographyTextBase>
      Suntem o echipă pasionată, dedicată furnizării de soluții inovative
      și personalizate pentru clienții noștri.
    </TypographyTextBase>
    <UButton>Descoperă mai mult</UButton>
  </HalfImageSection>
-->

<template>
	<section class="bg lg:flex space-x-16 lg:h-screen items-center">
		<NuxtImg
			:src="img.src"
			:alt="img.alt"
			format="webp"
			class="lg:w-[55%] h-[500px] lg:h-full object-cover"
		/>

		<div class="py-16 px-8 space-y-6 lg:pr-32">
			<slot>
				<TypographySectionTitle
					>Povestea Noastră</TypographySectionTitle
				>
				<TypographyTextBase
					>Lorem ipsum dolor sit amet consectetur. Nunc nunc rhoncus
					hendrerit in curabitur nisi. Pulvinar risus donec eget id
					consectetur pharetra porttitor suspendisse. Sed ut blandit
					nunc accumsan. Ac sit interdum rhoncus dignissim augue
					habitant augue quis tempus. Gravida dapibus facilisi vitae
					ut nulla aliquet tortor. Lorem ipsum dolor sit amet
					consectetur. Nunc nunc rhoncus hendrerit in curabitur nisi.
					Pulvinar risus donec eget id
				</TypographyTextBase>
				<UButton>Citește mai mult</UButton>
			</slot>
		</div>
	</section>
</template>

<script lang="ts" setup>
	const props = withDefaults(
		defineProps<{
			img?: { src: string; alt: string };
		}>(),
		{
			img: () => ({
				src: "/placeholder.png",
				alt: "Default background image",
			}),
		}
	);
</script>
