<script>
	export let title, options;
	let imgBody = "blue";
	let imgEyes = "blue";
	let imgShirt = "svelte";
	let imgAccessory = "mask";
	let accessoryWidth = "315px";
	let accessoryTop = "50px";
	let accessoryLeft = "49px";

	const setBody = body => {
		imgBody = body;
	}
	const setEyes = eyes => {
		imgEyes = eyes;
	}
	const setShirt = shirt => {
		imgShirt = shirt;
	}
	const setAccessory = (accessory, val) => {
		imgAccessory = accessory;
		accessoryWidth = val.width;
		accessoryTop = val.top;
		accessoryLeft = val.left;
	}
</script>

<h1>{title}</h1>

<div id="main">
	<section id="render">
		<img id="body" src="/assets/body/{imgBody}.svg" alt="the body of the planarian" />
		<img id="eyes" src="/assets/eyes/{imgEyes}.svg" alt="the eyes of the planarian" />
		<img id="shirt" src="/assets/shirts/{imgShirt}.svg" alt="the shirt of the planarian" />
		<img id="accessory" style='width:{accessoryWidth}; top:{accessoryTop}; left:{accessoryLeft};' src="/assets/accessories/{imgAccessory}.svg" alt="the accessory of the planarian" />
	</section>

	<section id="options">
		<div><strong>Body</strong></div>
		<div class="links">
		{#each options.body as body}
			<a href="/" on:click|preventDefault={setBody(body)}>{body}</a>
		{/each}
		</div>
		<br />
		<div><strong>Eyes</strong></div>
		<div class="links">
		{#each options.eyes as eyes}
			<a href="/" on:click|preventDefault={setEyes(eyes)}>{eyes}</a>
		{/each}
		</div>
		<br />
		<div><strong>Shirt</strong></div>
		<div class="links">
		{#each options.shirts as shirt}
			<a href="/" on:click|preventDefault={setShirt(shirt)}>{shirt}</a>
		{/each}
		</div>
		<br />
		<div><strong>Accessories</strong></div>
		<div class="links">
		{#each Object.entries(options.accessories) as [key, val]}
			<a href="/" on:click|preventDefault={setAccessory(key, val)}>{key}</a>
		{/each}
		</div>
		<br />
	</section>
</div>

<style>
	h1 {
		font-family: Helvetica, sans-serif;
	}
	#main {
		display: flex;
	}
	#render {
		position: relative;
	}
	#eyes {
		position: absolute;
		left: 110px;
		top: 40px;
	}
	#shirt {
		position: absolute;
		top: 170px;
		left: 112px;
	}
	#accessory {
		position: absolute;
		top: 48px;
		left: 45px;
	}
	#options {
		flex-grow: 1;
		padding-left: 60px;
	}
	.links {
		display: grid;
		grid-template-columns: 25% 25% 25% 25%;
		grid-row-gap: 20px;
	}
</style>