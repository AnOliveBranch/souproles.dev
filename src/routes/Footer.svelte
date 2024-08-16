<script>
	import github from '$lib/images/github-mark-white.svg';
</script>

<footer>
	<ul>
		<li>© 2024 AnOliveBranch — MIT License</li>
		<li>
			<a href="https://github.com/AnOliveBranch/anolivebranch.dev" target="_blank">
				<img src={github} alt="GitHub Logo" />Source
			</a>
		</li>
	</ul>
</footer>

<style>
	footer {
		border-top: 2px solid rgb(100, 166, 241);
		font-size: 1.25em;
	}

	footer,
	footer a {
		color: rgb(150, 150, 150);
	}

	ul {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 0 10%;
	}

	ul li {
		display: inline;
	}

	li img {
		height: 1em;
		padding-right: 0.5em;
		vertical-align: middle;
	}

	li a {
		text-decoration: none;
	}

	/*
	 * Mobile footer design
	 */
	@media screen and (max-width: 600px) {
		ul {
			flex-direction: column;
		}
	}
</style>
