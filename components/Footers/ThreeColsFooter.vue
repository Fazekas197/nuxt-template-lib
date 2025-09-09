<!--
  Component: ThreeColsFooter

  Description:
  A three-column footer with location and social links, contact details,
  and navigation links. Includes a full-width credit bar.
  Ideal for websites that need structured footer content with consistent
  branding, contact info, and accessibility support.

  Props:
  - title: string
      Section heading for the location block. Defaults to placeholder text.
  - location: string
      Address or location details. Defaults to placeholder text.
  - socials: Array<{ label: string, link: string, icon: string }>
      Social media icons with links and ARIA labels. Defaults to major platforms.
  - contacts: Array<{ icon: string, text: string }>
      Contact methods such as phone and email. Defaults to dummy data.
  - links: Array<{ text: string, link: string }>
      Internal navigation links. Defaults to Home, About, and Services.
  - credit: string (required)
      Bottom footer credit line. Shown full width.

  Example usage:
  <ThreeColsFooter
    title="Contactați-ne"
    location="Str. Exemplu 123, București"
    :socials="[
      { label: 'Facebook', link: 'https://facebook.com', icon: 'i-ph-facebook-logo' }
    ]"
    :contacts="[
      { icon: 'i-ph-phone', text: '+40 712 345 678' },
      { icon: 'i-ph-envelope-simple', text: 'contact@exemplu.ro' }
    ]"
    :links="[
      { text: 'Acasă', link: '/' },
      { text: 'Servicii', link: '/servicii' },
      { text: 'Contact', link: '/contact' }
    ]"
    credit="© 2024 Compania Exemplu. Toate drepturile rezervate. Dezvoltat de Fazekas Cosmin"
  />
-->

<template>
	<footer>
		<div
			class="lg:flex justify-between mx-auto p-16 lg:px-[7.5rem] space-y-10 lg:space-y-0 w-fit lg:w-full 2xl:w-3/4"
		>
			<!-- LOCATION + SOCIALS -->
			<div class="lg:space-y-6 space-y-4">
				<!-- Title & Location -->
				<div class="font-secondary space-y-3">
					<p class="text-lg lg:text-xl font-semibold">{{ title }}</p>
					<TypographyBaseTxt class="leading-snug">{{
						location
					}}</TypographyBaseTxt>
				</div>

				<!-- Social Buttons -->
				<div class="lg:space-x-6 space-x-4 space-y-2">
					<UButton
						v-for="social in socials"
						:key="social.label"
						:aria-label="social.label"
						:to="social.link"
						:icon="social.icon"
						class="rounded-full"
						size="xl"
						color="secondary"
					/>
				</div>
			</div>

			<!-- CONTACT -->
			<div class="font-secondary space-y-3">
				<p class="text-xl font-semibold">Contact</p>
				<div class="space-y-2">
					<div
						v-for="(contact, index) in contacts"
						:key="index"
						class="flex gap-x-2 items-center"
					>
						<UIcon :name="contact.icon" class="size-7" />
						<TypographyBaseTxt class="leading-snug">{{
							contact.text
						}}</TypographyBaseTxt>
					</div>
				</div>
			</div>

			<!-- LINKS -->
			<div class="font-secondary space-y-3">
				<p class="text-xl font-semibold">Alte Linkuri</p>
				<div class="space-y-2">
					<NuxtLink
						v-for="link in links"
						:key="link.link"
						:to="link.link"
						class="block lg:text-lg underline"
					>
						{{ link.text }}
					</NuxtLink>
				</div>
			</div>
		</div>

		<!-- CREDITS -->
		<div
			class="bg-black text-white text-center py-3 px-10 text-xs lg:text-base font-secondary"
		>
			<p>{{ credit }}</p>
		</div>
	</footer>
</template>

<script lang="ts" setup>
	type Btn = {
		label: string;
		link: string;
		icon: string;
	};

	type Contact = {
		icon: string;
		text: string;
	};

	type Link = {
		text: string;
		link: string;
	};

	const props = withDefaults(
		defineProps<{
			title?: string;
			location?: string;
			socials?: Btn[];
			contacts?: Contact[];
			links?: Link[];
			credit: string;
		}>(),
		{
			title: "Praesent vehicula dapibus",
			location: "Praesent vehicula dapibus vehicula dapibus",
			socials: () => [
				{ label: "instagram", link: "/", icon: "i-ph-instagram-logo" },
				{ label: "tiktok", link: "/", icon: "i-ph-tiktok-logo" },
				{ label: "facebook", link: "/", icon: "i-ph-facebook-logo" },
				{
					label: "whatsapp",
					link: "/",
					icon: "i-ph-whatsapp-logo-light",
				},
				{ label: "întrebări", link: "#FAQ", icon: "i-ph-question" },
			],
			contacts: () => [
				{ icon: "i-ph-phone", text: "0741 000 000" },
				{ icon: "i-ph-envelope-simple", text: "emailultau@gmail.com" },
			],
			links: () => [
				{ text: "Home", link: "/" },
				{ text: "About", link: "/about" },
				{ text: "Services", link: "/services" },
			],
			credit: "All Rights Reserved © Copyright 2024 ... | Developed by Fazekas Cosmin",
		}
	);
</script>
