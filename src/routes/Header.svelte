<script lang="ts">
	import { page } from '$app/stores';
	import { derived } from 'svelte/store';
	import github from '$lib/images/github.svg';

	const currentPath = derived(page, ($page) => $page.url.pathname);
</script>

<header>
	<div class="corner left-corner">
		<a href="/" title="AarambhJs Home">
		</a>
	</div>

	<nav class="navbar">
		<div class="navbar-brand">
			<h1 class="title">AarambhJs</h1>
		</div>
		<ul class="navbar-links">
			{#each [
				{ name: 'Home', href: '/' },
				{ name: 'About', href: '/about' }
			] as link}
				<li class="navbar-item" class:active={$currentPath === link.href}>
					<a href={link.href} aria-current={$currentPath === link.href ? 'page' : undefined}>
						{link.name}
					</a>
				</li>
			{/each}
		</ul>
	</nav>

	<div class="corner right-corner">
		<a href="https://github.com/Pjdeveloper896/AarambhJsS" target="_blank" rel="noopener" title="View on GitHub">
			<img src={github} alt="GitHub" />
		</a>
	</div>
</header>

<style>
	

	.corner {
		width: 4em;
		height: 4em;
	}

	.corner a {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
	}

	.corner img {
		width: 3em;
		height: 3em;
		object-fit: contain;
		border-radius: 50%;
		box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
		transition: transform 0.3s ease, box-shadow 0.3s ease;
	}

	.corner img:hover {
		transform: scale(1.1);
		box-shadow: 0 0 10px rgba(255, 62, 0, 0.4);
	}

	.navbar {
		display: flex;
		align-items: center;
		width: 100%;
		max-width: 800px;
		justify-content: center;
	}

	.navbar-brand .title {
		margin-right: 2rem;
		font-size: 1.5rem;
		font-weight: bold;
		color: #ff3e00;
	}

	.navbar-links {
		display: flex;
		gap: 1.5rem;
		list-style: none;
		margin: 0;
		padding: 0;
	}

	.navbar-item {
		position: relative;
	}

	.navbar-item a {
		text-decoration: none;
		color: #333;
		font-weight: 600;
		font-size: 1rem;
		transition: color 0.2s ease;
	}

	.navbar-item a:hover {
		color: #ff3e00;
	}

	.navbar-item.active a {
		color: #ff3e00;
	}

	.navbar-item.active::before {
		content: '';
		position: absolute;
		bottom: -0.4rem;
		left: 50%;
		transform: translateX(-50%);
		width: 6px;
		height: 6px;
		background: #ff3e00;
		border-radius: 50%;
	}
</style>
s