<!--
  Component: GridSection

  Description:
  A responsive grid layout displaying a list of icon + text items. 
  The layout adapts to screen size with 2 columns on small screens 
  and 3 columns × 2 rows on large screens. Ideal for feature lists, 
  service highlights, or value propositions.

  Props:
  - elems: Array<{ icon: string; text: string }>
      An array of objects, each containing:
        - icon: the name of the icon to display (compatible with UIcon)
        - text: the accompanying descriptive label or value
      Defaults to six placeholder items with thumbs-up icons and generic text.

  Example usage:
  <GridSection
    :elems="[
      { icon: 'i-heroicons-sparkles-20-solid', text: 'Design unic' },
      { icon: 'i-heroicons-shield-check-20-solid', text: 'Garanție inclusă' },
      { icon: 'i-heroicons-bolt-20-solid', text: 'Instalare rapidă' },
      { icon: 'i-heroicons-globe-alt-20-solid', text: 'Disponibil internațional' },
      { icon: 'i-heroicons-heart-20-solid', text: 'Clienți mulțumiți' },
      { icon: 'i-heroicons-cube-20-solid', text: 'Livrare sigură' }
    ]"
  />
-->

<template>
	<div
		class="grid grid-cols-2 md:grid-cols-3 md:grid-rows-2 gap-12 md:gap-16 lg:gap-24 w-fit mx-auto"
	>
		<div v-for="elem in elems" class="flex flex-col items-center w-fit">
			<UIcon :name="elem.icon" class="size-10 lg:size-15" />
			<TypographyTextXl>{{ elem.text }}</TypographyTextXl>
		</div>
	</div>
</template>

<script setup lang="ts">
	type Elem = {
		icon: string;
		text: string;
	};

	const props = withDefaults(
		defineProps<{
			elems?: Elem[];
		}>(),
		{
			elems: () => [
				{
					icon: "i-mage-thumbs-up-fill",
					text: "Lorem Ipsum",
				},
				{
					icon: "i-mage-thumbs-up-fill",
					text: "Lorem Ipsum",
				},
				{
					icon: "i-mage-thumbs-up-fill",
					text: "Lorem Ipsum",
				},
				{
					icon: "i-mage-thumbs-up-fill",
					text: "Lorem Ipsum",
				},
				{
					icon: "i-mage-thumbs-up-fill",
					text: "Lorem Ipsum",
				},
				{
					icon: "i-mage-thumbs-up-fill",
					text: "Lorem Ipsum",
				},
			],
		}
	);
</script>
