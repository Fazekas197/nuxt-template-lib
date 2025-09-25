<!--
  Component: PartenersSection

  Description:
  A centered section displaying a vertical decorative line, a title, 
  and a list of partner names. Partner names are displayed in a 
  responsive layout: stacked vertically on small screens and in a 
  horizontal row on larger screens. Useful for showcasing business 
  partners, collaborators, or sponsors.

  Props:
  - title: string
      The section heading text.
      Defaults to "Parteneri".

  - parteners: string[]
      An array of partner names to be displayed.
      Defaults to four placeholder values: ["Lorem Ipsum", "Lorem Ipsum", "Lorem Ipsum", "Lorem Ipsum"].

  Example usage:
  <PartenersSection
    title="Partenerii noștri"
    :parteners="[
      'OpenAI',
      'Google',
      'Microsoft',
      'Amazon'
    ]"
  />
-->

<template>
	<section class="space-y-12 text-center">
		<DecorativesVerticalLine />
		<TypographySectionTitle>{{ title }}</TypographySectionTitle>
		<div
			class="space-y-6 lg:flex lg:justify-center lg:gap-x-6 lg:space-y-0"
		>
			<TypographyTextXl v-for="partener in parteners">{{
				partener
			}}</TypographyTextXl>
		</div>
		<DecorativesVerticalLine />
	</section>
</template>

<script lang="ts" setup>
	const props = withDefaults(
		defineProps<{
			title?: string;
			parteners?: string[];
		}>(),
		{
			title: "Parteneri",
			parteners: () => [
				"Lorem Ipsum",
				"Lorem Ipsum",
				"Lorem Ipsum",
				"Lorem Ipsum",
			],
		}
	);
</script>
