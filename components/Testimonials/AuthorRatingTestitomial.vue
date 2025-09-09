<!--
  Component: AuthorRatingTestimonial

  Description:
  A centered testimonial block that includes a dynamic star rating, 
  author name, and testimonial text. Ideal for showcasing customer 
  feedback or expert opinions on landing pages, product pages, or 
  review sections.

  Props:
  - starIcon: string
      The icon name used to represent a single star.
      Defaults to "i-material-symbols-light-kid-star-sharp".
      Compatible with UIcon (e.g., from UnoCSS or Nuxt UI).

  - rating: number
      Number of stars to display (e.g., 5 for a 5-star rating).
      Defaults to 5.

  - author: string
      Name of the person giving the testimonial.
      Displayed beneath the stars. Defaults to "Lorem Ipsum".

  - testimonial: string
      The main testimonial content or quote.
      Rendered as a paragraph below the author name.
      Defaults to a placeholder text.

  Example usage:
  <AuthorRatingTestimonial
    starIcon="i-heroicons-star-20-solid"
    :rating="4"
    author="Andreea Popescu"
    testimonial="Un serviciu excelent! Totul a fost profesionist și plăcut."
  />
-->

<template>
	<div class="lg:w-1/2 mx-auto space-y-6">
		<div>
			<UIcon
				:name="starIcon"
				v-for="item in Array(rating).keys()"
				class="size-10 lg:size-15 bg-yellow-300"
			/>
			<h4 class="text-3xl lg:text-4xl">{{ author }}</h4>
		</div>

		<TypographyBaseTxt>{{ testimonial }}</TypographyBaseTxt>
	</div>
</template>

<script lang="ts" setup>
	const props = withDefaults(
		defineProps<{
			starIcon?: string;
			rating?: number;
			author?: string;
			testimonial?: string;
		}>(),
		{
			starIcon: "i-material-symbols-light-kid-star-sharp",
			rating: 5,
			author: "Lorem Ipsum ",
			testimonial:
				"Praesent vehicula dapibus neque dolor sit amet Praesent vehicula dapibus neque dolor sit amet Praesent vehicula dapibus neque dolor sit amet Praesent vehicula dapibus neque dolor sit amet Praesent vehicula dapibus neque dolor sit amet",
		}
	);
</script>
