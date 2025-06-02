<script lang="ts">
	import { fade, fly } from 'svelte/transition';
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcomeFallback from '$lib/images/svelte-welcome.png';

	let articleVisible = false;

	function inView(node: HTMLElement) {
		const observer = new IntersectionObserver(([entry]) => {
			if (entry.isIntersecting) {
				articleVisible = true;
				observer.disconnect();
			}
		});
		observer.observe(node);
		return {
			destroy() {
				observer.disconnect();
			}
		};
	}
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
	<link
		rel="stylesheet"
		href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css"
	/>
</svelte:head>

<section class="hero is-link is-fullheight" in:fade>
	<div class="hero-body">
		<div>
			<p class="title">Aarambh js</p>
			<br />
			<p class="subtitle">"from hello world to big apps effortlessly"</p>
			<br />
			<figure class="media-left">
				<p class="image" style="width: 100px; height: 100px;">
					<img
						src="https://pjdeveloper896.github.io/AarambhJS/AarambhJS%20Software%20Framework%20Logo.png"
						alt="logo"
					/>
				</p>
				<br />
				<button class="button is-success is-rounded">
					<a class="btn is-primary is-rounded" href = "https://pjdeveloper896.github.io/AarambhJS/">get started</a>
				</button>
			</figure>
		</div>
	</div>
</section>

{#if articleVisible}
<article
	class="media"
	in:fly={{ y: 50, duration: 800 }}

>
	<figure class="media-left">
		<p class="image" style="width: 100px; height: 100px;">
			<img
				src="https://images.pexels.com/photos/20220477/pexels-photo-20220477/free-photo-of-close-up-shot-of-beautiful-fashion-model-happy.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2"
				alt="logo"
			/>
		</p>
	</figure>
	<div class="media-content">
		<div class="content">
			<p>
				<strong>AarambhJs</strong>
				<br />
				A New and Modern <span>JavaScript</span> framework.
				<br />
				AarambhJS is a beginner-friendly JavaScript UI framework that supports Virtual DOM
				rendering, JSX-like syntax, and simple client-side routing — all in one lightweight
				script.
			</p>
		</div>
		<nav class="level is-mobile">
			<div class="level-left">
				<a class="level-item"><span class="icon is-small"><i class="fas fa-reply"></i></span></a>
				<a class="level-item"><span class="icon is-small"><i class="fas fa-retweet"></i></span></a>
				<a class="level-item"><span class="icon is-small"><i class="fas fa-heart"></i></span></a>
			</div>
		</nav>
	</div>
	<div class="media-right">
		<button class="delete"></button>
	</div>
</article>
{/if}

<!-- invisible watcher triggers scroll animation -->
<div use:inView style="height: 1px;"></div>

<!-- Footer with interactive links -->
<footer class="footer has-text-centered p-4" in:fade>
	<p>
		<a
			href="https://github.com/pjdeveloper896/AarambhJS"
			target="_blank"
			rel="noopener"
			class="icon-text mx-2"
		>
			<span class="icon"><i class="fab fa-github"></i></span>
			<span>GitHub</span>
		</a>

		<a
			href="https://www.npmjs.com/package/aarambhjs"
			target="_blank"
			rel="noopener"
			class="icon-text mx-2"
		>
			<span class="icon"><i class="fab fa-npm"></i></span>
			<span>npm</span>
		</a>

		<a
			href="https://dev.to/Pjdeveloper896"
			target="_blank"
			rel="noopener"
			class="icon-text mx-2"
		>
			<span class="icon"><i class="fab fa-dev"></i></span>
			<span>Dev.to</span>
		</a>
	</p>
</footer>

<style>
	html {
		scroll-behavior: smooth;
	}
	.mx-2 {
		margin-left: 0.75rem;
		margin-right: 0.75rem;
	}
</style>
