<script>
	import RssIcon from '$lib/icons/rss.svelte';
	import EmailIcon from '$lib/icons/socials/email.svelte';
	import GitHubIcon from '$lib/icons/socials/github.svelte';
	import LinkedInIcon from '$lib/icons/socials/linkedin.svelte';
	import MastodonIcon from '$lib/icons/socials/mastodon.svelte';
	// import TelegramIcon from '$lib/icons/socials/telegram.svelte';
</script>

<div class="socials">
<!--	<a
		href="https://hachyderm.io/@fantinel"
		target="_blank"
		rel="me noreferrer"
		title="Say Hi on Mastodon"
	>
		<MastodonIcon />
	</a>-->
	<a
		href="https://github.com/LinhNC"
		target="_blank"
		rel="me noopener noreferrer"
		title="See my GitHub profile"
	>
		<GitHubIcon />
	</a>
	<a
		href="https://www.linkedin.com/in/LinhNC/"
		target="_blank"
		rel="me noopener noreferrer"
		title="Connect on LinkedIn"
	>
		<LinkedInIcon />
	</a>
	<a
		href="mailto:info@linhgo.com"
		target="_blank"
		rel="noopener noreferrer"
		title="Send an email to info@linhgo.com"
	>
		<EmailIcon />
	</a>
	<a href="/rss.xml" target="_blank" rel="noopener noreferrer" title="Subscribe to my RSS Feed">
		<RssIcon />
	</a>
</div>

<style lang="scss">
	@import '../../scss/breakpoints.scss';
	.socials {
		display: flex;
		align-items: center;
		gap: 20px;

		a {
			transition: all 0.2s ease-in-out;
			width: 24px;
			color: var(--color--text);
			fill: var(--color--text);

			&:hover {
				color: var(--color--primary);
				fill: var(--color--primary);
				filter: drop-shadow(0px 0px 3px var(--color--primary));
			}
		}
	}
</style>
