<script lang="ts">
	import { t } from 'svelte-i18n';
	import Button from '../button.svelte';

	import { page } from '$app/stores';

	$: isContactPage = $page.url.pathname === '/contact';
</script>

<footer>
	<div class="copyright">
		<p>{$t('footer.copyright')}</p>
		<p>{$t('footer.credits')} <a href="/about-me">Sem Van Broekhoven</a></p>
	</div>
	{#if !isContactPage}
		<div class="contact">
			<Button href="/contact">{$t('footer.email')}</Button>
			<div class="socials">
				<a href="https://github.com/dotsem" target="_blank" aria-label="Github"
					><i class="fa-brands fa-github"></i></a
				>
				<a href="https://www.linkedin.com/in/sem-van-broekhoven/" target="_blank" aria-label="LinkedIn"
					><i class="fa-brands fa-linkedin"></i></a
				>
				<a href="https://www.instagram.com/sem_van_broekhoven/" target="_blank" aria-label="Instagram"
					><i class="fa-brands fa-instagram"></i></a
				>
				<a href="https://www.facebook.com/profile.php?id=100089528472654" target="_blank" aria-label="Facebook"
					><i class="fa-brands fa-facebook"></i></a
				>
			</div>
		</div>
	{/if}
</footer>

<style>
	footer {
		padding: 48px 2rem;
		width: 100%;
		background: var(--nav);
		display: flex;
		flex-wrap: wrap-reverse;
		justify-content: space-evenly;
		align-items: center;

		> div {
			display: flex;
			align-items: center;
			justify-content: center;
			flex-wrap: wrap;
			width: fit-content;

			&.copyright {
				display: flex;
				flex-direction: column;
				text-align: center;

				p {
					padding: 4px 0;
				}

				a {
					transition: color 500ms;
					color: var(--secondary);
					font-weight: 800;

					&:hover {
						transition: color 500ms;
						color: var(--secondary);
					}
				}
			}

			.socials {
				display: flex;
				gap: 16px;

				> a {
					transition: opacity 500ms;
					height: fit-content;
					font-size: 36px;
					color: var(--text);
					opacity: 1;

					i {
						transition: transform 500ms;
					}
				}

				&:has(a:hover) a:not(:hover) {
					transition: opacity 500ms;
					opacity: 0.5;

					i {
						transform: scale(0.8);

						transition: transform 500ms;
					}
				}

				a:hover {
					transition: transform 500ms;

					transition:
						color 500ms,
						opacity 500ms;
					color: var(--secondary);
					opacity: 1;

					i {
						transition: transform 500ms;
						transform: scale(1.1);
					}
				}
			}
		}
	}

	@media only screen and (max-width: 899px) {
		footer {
			> div {
				padding-bottom: 16px;

				&:last-child {
					border-bottom: 3px solid var(--primary);
				}
			}

		}
	}
</style>
