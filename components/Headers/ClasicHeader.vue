<!--
  Component: ResponsiveHeader

  Description:
  A responsive and accessible website header with a logo slot, primary navigation links,
  and a mobile menu toggle. The component supports both mobile and desktop layouts.
  On mobile, it displays a full-screen slide-in menu with animated hamburger toggle.
  On desktop, links are shown inline. Ideal for websites needing a modern,
  mobile-first navigation experience.

  Props:
  - links: Array<{ text: string; link: string; }>
      An array of navigation links. Each item must include:
        - text: the label to be shown in the menu (string)
        - link: the route path (string)
      Defaults to two placeholder links: [{ text: "link 1", link: "/" }, { text: "link 2", link: "/" }]

  Slots:
  - logo
      Slot for injecting a custom logo or branding element.
  - links
      Optional slot to append additional items (e.g., buttons or icons) after the link list,
      both on mobile and desktop versions.

  Example usage:
  <ResponsiveHeader
    :links="[
      { text: 'Acasă', link: '/' },
      { text: 'Servicii', link: '/servicii' },
      { text: 'Contact', link: '/contact' }
    ]"
  >
    <template #logo>
      <img src="/logo.svg" alt="Logo companie" class="h-10" />
    </template>

    <template #links>
      <UButton color="secondary" variant="outline" to="tel:+40700000000">
        Sunați-ne
      </UButton>
    </template>
  </ResponsiveHeader>
-->

<template>
	<header
		class="w-full px-6 py-3 lg:px-12 lg:py-6 flex items-center justify-between text-black z-50"
	>
		<NuxtLink
			to="/"
			class="flex items-center gap-x-3 z-50"
			@click="navOpen = false"
		>
			<slot name="logo"> LOGO </slot>
		</NuxtLink>

		<button
			@click="navOpen = !navOpen"
			aria-label="Toggle navigation"
			class="relative w-8 h-8 flex flex-col z-50 justify-center items-center gap-1.5 group lg:hidden"
		>
			<span
				:class="[
					'w-8 h-0.5 bg-black transition-transform duration-300',
					navOpen ? 'rotate-45 translate-y-2' : '',
				]"
			/>
			<span
				:class="[
					'w-8 h-0.5 bg-black transition-opacity duration-300',
					navOpen ? 'opacity-0' : 'opacity-100',
				]"
			/>
			<span
				:class="[
					'w-8 h-0.5 bg-black transition-transform duration-300',
					navOpen ? '-rotate-45 -translate-y-2' : '',
				]"
			/>
		</button>

		<nav
			:class="[
				'fixed inset-y-0 left-0 w-full bg-white flex flex-col px-6 gap-y-6 transform transition-transform duration-300 ease-out z-40 lg:hidden',
				navOpen ? 'translate-x-0' : '-translate-x-full',
			]"
			:style="{ paddingTop: `${headerHeight + 60}px` }"
		>
			<NuxtLink
				v-for="link in links"
				active-class="underline decoration-wavy underline-offset-4"
				:to="link.link"
				class="text-xl font-secondary"
				@click="navOpen = false"
				>{{ link.text }}</NuxtLink
			>
			<slot name="links">
				<UButton color="secondary" variant="outline" to="tel:"
					>telefon</UButton
				>
			</slot>
		</nav>

		<nav class="text-lg hidden lg:block space-x-6 z-30">
			<NuxtLink
				v-for="link in links"
				:to="link.link"
				active-class="underline decoration-wavy underline-offset-4"
				class="hover:text-beige transition decoration-2 font-secondary"
				>{{ link.text }}</NuxtLink
			>
			<slot name="links">
				<UButton color="secondary" variant="outline" to="tel:"
					>telefon</UButton
				>
			</slot>
		</nav>
	</header>
</template>

<script setup lang="ts">
	type Link = {
		text: string;
		link: string;
	};

	const props = withDefaults(
		defineProps<{
			links?: Link[];
		}>(),
		{
			links: () => [
				{ text: "link 1", link: "/" },
				{ text: "link 2", link: "/" },
			],
		}
	);

	const navOpen = ref(false);

	watch(navOpen, (isOpen) => {
		if (isOpen) {
			document.body.classList.add("overflow-hidden");
		} else {
			document.body.classList.remove("overflow-hidden");
		}
	});

	const headerHeight = ref(0); // Reactive variable to store header height

	// Function to calculate header height
	const updateHeaderHeight = () => {
		const headerElement = document.querySelector("header");
		if (headerElement) {
			headerHeight.value = headerElement.offsetHeight;
		}
	};

	onMounted(() => {
		// Calculate height initially
		updateHeaderHeight();
		// Recalculate on window resize (important for responsive headers)
		window.addEventListener("resize", updateHeaderHeight);
	});

	onUnmounted(() => {
		// Clean up event listener when component is unmounted
		window.removeEventListener("resize", updateHeaderHeight);
	});
</script>
