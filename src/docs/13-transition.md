---
title: Transition
description: Transition CSS Classes for Svelte
openGraph:
  type: website
  url: https://captaincodeman.github.io/svelte-headlessui/transition
  title: Tabs
  images:
  -
    url: /svelte-headlessui/transition.png
    width: 1332
    height: 756
twitter:
  card: summary_large_image
  site: captaincodeman
  title: Transition 🚀 Svelte-HeadlessUI
  description: Headless Transition for Svelte
  image: /svelte-headlessui/transition.png
---

# Transition

The Transition component lets you add enter/leave transitions to conditionally rendered elements, using CSS classes to control the actual transition styles in the different stages of the transition.

<iframe class="w-full h-[378px] rounded-xl border-none" src="./example/transition"></iframe>
<a href="./example/transition" target="_blank">
	Open in separate tab
</a>

NOTE: the transition element is published as a separate package `svelte-transition`

## Example

```svelte
<script lang="ts">
	import Transition from 'svelte-transition'

	export let show = true

	function resetIsShowing() {
		show = false
		setTimeout(() => (show = true), 500)
	}
</script>

<div class="p-16 relative flex flex-col items-center justify-center m-8 rounded-xl overflow-hidden">
	<div class="w-32 h-32">
		<Transition
			{show}
			appear
			enter="duration-[400ms]"
			enterFrom="opacity-0 rotate-[-120deg] scale-50"
			enterTo="opacity-100 rotate-0 scale-100"
			leave="duration-200 transition ease-in-out"
			leaveFrom="opacity-100 rotate-0 scale-100"
			leaveTo="opacity-0 scale-95"
		>
			<div class="w-full h-full bg-white rounded-md shadow-lg" />
		</Transition>
	</div>
	<button
		on:click={resetIsShowing}
		disabled={!show}
		class="flex items-center px-3 py-2 mt-8 text-sm font-medium text-white transition transform bg-black rounded-full active:bg-opacity-40 hover:scale-105 hover:bg-opacity-30 focus:outline-none bg-opacity-20"
	>
		<svg viewBox="0 0 20 20" fill="none" class="w-5 h-5 opacity-70">
			<path
				d="M14.9497 14.9498C12.2161 17.6835 7.78392 17.6835 5.05025 14.9498C2.31658 12.2162 2.31658 7.784 5.05025 5.05033C7.78392 2.31666 12.2161 2.31666 14.9497 5.05033C15.5333 5.63385 15.9922 6.29475 16.3266 7M16.9497 2L17 7H16.3266M12 7L16.3266 7"
				stroke="currentColor"
				stroke-width="1.5"
			/>
		</svg>

		<span class="ml-3">Click to transition</span>
	</button>
</div>
```
