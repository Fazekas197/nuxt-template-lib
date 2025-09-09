<!--
  Component: FAQSection

  Description:
  A frequently asked questions (FAQ) section with a customizable title and
  a list of expandable/collapsible questions using a lazy-loaded accordion.
  Ideal for product pages, help centers, or service websites that need
  a clean and responsive way to address common user inquiries.

  Props:
  - title: string
      The main heading of the FAQ section. Defaults to "FAQ".
  - questions: Array<{ label: string; content: string; }>
      An array of question and answer pairs. Each item must have:
        - label: the question text (string)
        - content: the answer text (string)
      Defaults to two placeholder items.

  Example usage:
  <FAQSection
    title="Întrebări frecvente"
    :questions="[
      { label: 'Care este programul de lucru?', content: 'Programul este de luni până vineri, între 09:00 și 17:00.' },
      { label: 'Cum pot face o programare?', content: 'Ne puteți contacta prin telefon sau email pentru a stabili o programare.' }
    ]"
  />
-->

<template>
	<div
		id="FAQ"
		class="px-6 py-8 md:px-[120px] xl:px-60 lg:py-16 space-y-6 2xl:w-3/4 mx-auto"
	>
		<TypographySectionTitle class="text-center md:text-start">{{
			title
		}}</TypographySectionTitle>

		<LazyUAccordion
			hydrate-on-interaction
			:items="questions"
			:ui="accordionUI"
		/>
	</div>
</template>

<script setup lang="ts">
	type Faq = {
		label: string;
		content: string;
	};

	const props = withDefaults(
		defineProps<{
			title: string;
			questions: Faq[];
		}>(),
		{
			title: "FAQ",
			questions: () => [
				{ label: "Question 1", content: "Answear 1" },
				{ label: "Question 2", content: "Answear 2" },
			],
		}
	);

	const accordionUI = {
		root: "space-y-6",
		item: "border-2 border-l-0 border-r-0 border-[#B4BCB9] last:border-b-2",
		label: "text-lg lg:text-xl font-secondary font-normal",
		body: "font-secondary !text-base lg:!text-lg",
	};
</script>
