<script>
	import { page } from '$app/stores';
	import { onMount } from 'svelte';
	import triangleVertical from '$lib/images/triangle-vertical.svg';
	import triangleHorizonal from '$lib/images/triangle-horizontal.svg';
	import logoHorizonal from '$lib/images/logo-horizonal.png';
	import logoOnly from '$lib/images/logo-only.png';
	import hamburger from '$lib/images/hamburger.svg';
	import closeHamburger from '$lib/images/close-hamburger.svg';

	let currentPage = '';
	switch ($page.url.pathname) {
		case '/projects':
			currentPage = 'Projects';
			break;
		case '/about':
			currentPage = 'About';
			break;
		case '/contact':
			currentPage = 'Contact';
			break;
		default:
			currentPage = 'Home';
	}

	let innerWidth = 0;
	let navShown = true;

	onMount(() => {
		navShown = innerWidth > 600;
	});

	function showNav() {
		navShown = true;
	}

	function hideNav() {
		if (innerWidth < 600) {
			navShown = false;
		}
	}
</script>

<svelte:window bind:innerWidth />

<header>
	<div id={navShown ? 'topBarShown' : 'topBarHidden'}>
		{#if navShown}
			<button on:click={hideNav} class="hamburger mobile" id="hamburger-close">
				<img class="mobile" src={closeHamburger} alt="Hamburger Close Icon" />
			</button>
		{:else}
			{#if currentPage == 'Home'}
				<img id="navLogo" class="mobile logo" src={logoHorizonal} alt="AnOliveBranch Logo" />
			{:else}
				<div id="logoAndText">
					<img id="navLogo" class="mobile logo" src={logoOnly} alt="AnOliveBranch Logo" />
					<p class="mobile">{currentPage}</p>
				</div>
			{/if}
			<button on:click={showNav} class="hamburger mobile" id="hamburger-open">
				<img class="mobile" src={hamburger} alt="Hamburger Icon" />
			</button>
		{/if}
	</div>
	<nav>
		{#if navShown}
			<ul id="navList">
				<li aria-current={$page.url.pathname === '/' ? 'page' : undefined}>
					<a
						href="/"
						on:click={() => {
							currentPage = 'Home';
							hideNav();
						}}
					>
						<img class="page-indicator mobile" src={triangleHorizonal} alt="Current Page" />
						<img class="logo" src={logoHorizonal} alt="AnOliveBranch Logo" />
						<img class="page-indicator desktop" src={triangleVertical} alt="Current Page" />
					</a>
				</li>
				<li aria-current={$page.url.pathname === '/projects' ? 'page' : undefined}>
					<a
						href="/projects"
						on:click={() => {
							currentPage = 'Projects';
							hideNav();
						}}
					>
						<img class="page-indicator mobile" src={triangleHorizonal} alt="Current Page" />
						Projects
						<img class="page-indicator desktop" src={triangleVertical} alt="Current Page" />
					</a>
				</li>
				<li aria-current={$page.url.pathname === '/about' ? 'page' : undefined}>
					<a
						href="/about"
						on:click={() => {
							currentPage = 'About';
							hideNav();
						}}
					>
						<img class="page-indicator mobile" src={triangleHorizonal} alt="Current Page" />
						About
						<img class="page-indicator desktop" src={triangleVertical} alt="Current Page" />
					</a>
				</li>
				<li aria-current={$page.url.pathname === '/contact' ? 'page' : undefined}>
					<a
						href="/contact"
						on:click={() => {
							currentPage = 'Contact';
							hideNav();
						}}
					>
						<img class="page-indicator mobile" src={triangleHorizonal} alt="Current Page" />
						Contact
						<img class="page-indicator desktop" src={triangleVertical} alt="Current Page" />
					</a>
				</li>
			</ul>
		{/if}
	</nav>
</header>

<style>
	nav {
		text-align: center;
		border-bottom: 2px solid rgb(100, 166, 241);
		position: relative;
	}

	ul {
		display: flex;
		justify-content: space-around;
		align-items: stretch;
		margin: 0;
		padding: 0;
	}

	ul li {
		display: flex;
		padding: 0;
		font-size: 1.5em;
		position: relative;
		flex: 1;
	}

	li a {
		color: white;
		text-decoration: none;
		transition: 0.5s;
		padding: 1em 0;
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		box-sizing: border-box;
	}

	li .page-indicator {
		display: none;
		position: absolute;
		width: 20px;
		height: auto;
	}

	li .logo {
		height: 2.5em;
		margin: auto;
	}

	li a:hover {
		background-color: rgb(120, 186, 255);
	}

	/*
	 * Mobile navigation design
	 */
	@media screen and (max-width: 60rem) {
		.desktop {
			display: none;
		}

		nav ul {
			flex-direction: column;
		}

		li a {
			flex-direction: row;
		}

		li .page-indicator {
			bottom: 50%;
			left: 1em;
			transform: translateY(50%);
		}

		li[aria-current='page'] .page-indicator.mobile {
			display: block;
		}

		#topBarShown,
		#topBarHidden {
			margin: 0.5em;
			display: flex;
			align-items: center;
		}

		#topBarShown {
			justify-content: right;
		}

		#topBarHidden {
			justify-content: space-between;
		}

		#logoAndText {
			display: flex;
			align-items: center;
			height: 2.5em;
		}

		#logoAndText p {
			margin-left: 0.5em;
			font-family: Arial, Helvetica, sans-serif;
		}

		#navLogo {
			height: 2.5em;
		}

		button {
			cursor: pointer;
			background: none;
			border: none;
		}
	}

	/*
	 * Desktop navigation design
	 */
	@media screen and (min-width: 60rem) {
		.mobile {
			display: none;
		}

		nav ul {
			flex-direction: row;
		}

		li a {
			flex-direction: column;
		}

		li .page-indicator {
			bottom: 0;
			left: 50%;
			transform: translateX(-50%);
		}

		li[aria-current='page'] .page-indicator.desktop {
			display: block;
		}
	}
</style>
