<script lang="ts">
	import Prism from 'prismjs';
	import 'prismjs/components/prism-json';
	import 'prismjs/components/prism-bash';
	import 'prismjs/components/prism-css';
	import 'prismjs/components/prism-typescript';
	import 'prismjs/components/prism-git';
	import 'prismjs/components/prism-javascript';
	import 'prismjs/components/prism-jsx';
	import 'prismjs/components/prism-markdown';
	import 'prismjs/components/prism-powershell';
	import 'prismjs/components/prism-scss';
	import 'prism-svelte';
	Prism.manual = true;
	const prism = Prism as any;

	export let filename: string | undefined = undefined;
	export let lang: string;
	export let code: string | undefined = undefined;
	export let fullBleed: boolean | undefined = undefined;

	let copySuccess = false;

	const copyToClipboard = async () => {
		if (code) {
			try {
				await navigator.clipboard.writeText(code);
				copySuccess = true;
				setTimeout(() => (copySuccess = false), 2000);
			} catch (err) {
				console.error('Failed to copy: ', err);
			}
		}
	};
</script>

<div class="code-block" class:full-bleed={fullBleed}>
	{#if filename}
		<div class="filename">{filename}</div>
	{/if}
	<button class="copy-button" on:click={copyToClipboard}>
		{#if copySuccess}
			Copied!
		{:else}
			<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" viewBox="0 0 16 16">
				<path d="M10 1H2a1 1 0 0 0-1 1v10.5a.5.5 0 0 0 .5.5H4v1a1 1 0 0 0 1 1h8a1 1 0 0 0 1-1V5a1 1 0 0 0-1-1h-1V2a1 1 0 0 0-1-1zM9 2v3H4V2h5zM2 2h1v3H2V2zm1 10H2V6h1v6zm1 0V6h5v6H4zm6 0H9V6h1v6zm1 0V6h1v6h-1zm1 0h1V6h-1v6z"/>
			</svg>
		{/if}
	</button>
	{#if lang}
		<div class="lang">{lang}</div>
	{/if}
	{#if code}
		{#if lang}
			<pre class={`language-${lang}`}>{@html Prism.highlight(
					code,
					prism.languages[lang],
					lang
				)}</pre>
		{:else}
			<pre>{code}</pre>
		{/if}
	{:else}
		<slot />
	{/if}
</div>

<style lang="scss">
	.code-block {
		display: block;
		position: relative;
		background-color: var(--color--code-background);
		color: var(--color--code-text);
		font-family: var(--font--mono);
		font-size: 1rem;
		line-height: 1.33em;
		border-radius: 8px;
		box-shadow: var(--card-shadow);

		padding: 30px 15px;
		margin: 30px 0;

		:global(pre) {
			font-family: var(--font--mono);
			overflow-x: auto;
			scrollbar-color: var(--color--primary) var(--color--primary-tint);
			scrollbar-width: thin;
			padding-bottom: 5px;

			tab-size: 0;

			&::-webkit-scrollbar {
				height: 8px;
			}
			&::-webkit-scrollbar-thumb {
				background: var(--color--primary);
				&:hover {
					background: var(--color--primary-shade);
				}
			}
		}

		.lang {
			position: absolute;
			right: 0;
			top: -15px;
			background: inherit;
			border-radius: 8px;
			padding: 5px 10px;
			z-index: 2;
			font-size: 0.85em;
		}

		.filename {
			background: inherit;
			border-top-left-radius: 8px;
			border-top-right-radius: 8px;
			margin-bottom: -2px;
			padding: 5px 10px;
			position: absolute;
			left: 0px;
			top: -15px;
			z-index: 1;
		}

		.copy-button {
			position: absolute;
			bottom: 10px;
			right: 10px;
			background: var(--color--primary);
			color: white;
			border: none;
			border-radius: 4px;
			padding: 5px 10px;
			cursor: pointer;
			font-size: 0.85em;
			z-index: 3;
			display: flex;
			align-items: center;
			gap: 5px;

			&:hover {
				background: var(--color--primary-shade);
			}
		}
	}
</style>
