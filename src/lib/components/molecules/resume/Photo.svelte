<script lang="ts">
	import Image from '$lib/components/atoms/Image.svelte';
</script>

<Image
	additionalClass="resume-photo light"
	src="/images/resume-avatar.png"
	alt="Linh's Avatar"
	skipSrcset
/>
<Image
	additionalClass="resume-photo dark"
	src="/images/resume-avatar-dark.png"
	alt="Linh's Avatar"
	skipSrcset
/>

<style lang="scss">
	:global(img.resume-photo) {
		border-radius: 50%;
		width: 200px !important;
		height: 200px !important;
		box-sizing: border-box;
	}

	:global(.resume-photo.dark) {
		border: 3px solid var(--color--primary-shade);
		object-fit: cover;
	}

	:global([data-theme='dark']) :global(.resume-photo.light) {
		display: none;
	}

	:global([data-theme='light']) :global(.resume-photo.dark) {
		display: none;
	}

	// If data-theme is 'auto', use prefers-color-scheme
	:global([data-theme='auto']) :global(.resume-photo.light) {
		@media (prefers-color-scheme: dark) {
			display: none;
		}
	}

	:global([data-theme='auto']) :global(.resume-photo.dark) {
		@media (prefers-color-scheme: light), (prefers-color-scheme: no-preference) {
			display: none;
		}
	}
</style>
