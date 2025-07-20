<template>
	<div
		class="xl:flex xl:w-3/4 w-full flex-col xl:flex-row space-y-6 gap-6 xl:gap-12"
	>
		<NuxtImg
			:src="img.src"
			:alt="img.alt"
			class="xl:h-full w-full xl:w-1/3 aspect-square xl:aspect-video object-cover"
		/>

		<div class="space-y-3 xl:space-y-4">
			<h2 class="text-2xl xl:text-3xl leading-snug tracking-tight">
				{{ title }}
			</h2>
			<p class="text-base xl:text-lg leading-relaxed">
				{{ text }}
			</p>
			<UButton v-if="cta" :to="cta.link" class="self-start mt-2">
				{{ cta.title }}
			</UButton>
		</div>
	</div>
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
