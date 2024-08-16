<script>
	export let img = '';
	export let link = '';
	export let title = '';
	export let details = 'Some details';

	let side = 'front';

	function showBack() {
		side = 'back';
	}

	function showFront() {
		side = 'front';
	}
</script>

{#if side == 'front'}
	<div id="front">
		<a href={link} target="_blank">
			<h1>{title}</h1>
			<img src={img} alt={title} />
		</a>
		<button on:click={showBack}>About</button>
	</div>
{:else}
	<div id="back">
		<a href={link} target="_blank">
			<h1>{title}</h1>
			<p id="details">{details}</p>
		</a>
		<button on:click={showFront}>Back</button>
	</div>
{/if}

<style>
	div#front,
	div#back {
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		width: 200px;
		height: 300px;
		background-color: rgb(40, 40, 40);
		border-radius: 10%;
		border: 2px solid rgb(35, 35, 35);
		box-shadow: -3px 3px 5px 10px rgb(35, 35, 35);
	}

	a,
	button {
		border: 2px solid rgb(40, 40, 40);
	}

	a:hover,
	button:hover {
		border: 2px solid rgb(100, 166, 241);
	}

	p,
	a,
	button {
		font-family: Georgia, 'Times New Roman', Times, serif;
		text-align: center;
	}

	a {
		text-decoration: none;
		color: white;
		height: 200px;
		display: flex;
		flex-direction: column;
		padding: 0.5em;
	}

	a img,
	a p {
		width: 150px;
		object-fit: contain;
		margin: auto;
	}

	button {
		background: none;
		color: white;
		font-size: 1.5em;
		cursor: pointer;
		width: 100%;
		padding: 1em;
		border: none;
		border-top: 2px solid rgb(40, 40, 40);
	}

	a:hover {
		background-color: rgb(50, 50, 50);
		border-top-left-radius: 10%;
		border-top-right-radius: 10%;
	}

	button:hover {
		background-color: rgb(50, 50, 50);
		border-bottom-left-radius: 10%;
		border-bottom-right-radius: 10%;
	}

	h1 {
		font-size: 1.5em;
		font-weight: 100;
	}
</style>
