<script lang="ts">
	// Pythagorean calculator
	let ptgrc_choice = 0;

	// Search for Hypotenuse
	let ptgrc_0_opp_val = 0;
	let ptgrc_0_add_val = 0;
	$: hres = Math.sqrt(ptgrc_0_add_val ** 2 + ptgrc_0_opp_val ** 2);

	// Search for Opposite/Adjacent
	let ptgrc_1_hyp_val = 0;
	let ptgrc_1_ehr_val = 0; // ehr is short for either; either adjacent or opposite.
	$: ehres = Math.sqrt(ptgrc_1_hyp_val ** 2 - ptgrc_1_ehr_val ** 2);
</script>

<div class="inline-block">
	<h1 class="font-extrabold text-4xl">Pythagoras Calculator</h1>
	<button
		on:click={() => (ptgrc_choice = 0)}
		class="my-1 px-2 py-1 focus:px-5 transition-all {ptgrc_choice == 0
			? 'bg-black text-white'
			: 'border border-black bg-transparent text-black'}">Search for Hypotenuse</button
	>
	<button
		on:click={() => (ptgrc_choice = 1)}
		class="my-1 px-2 py-1 focus:px-5 transition-all {ptgrc_choice == 1
			? 'bg-black text-white'
			: 'border border-black bg-transparent text-black'}">Search for Opposite/Adjacent</button
	>
	<br />
	{#if ptgrc_choice === 0}
		<p>
			{hres.toString().match(/\./) ? `√${ptgrc_0_add_val ** 2 + ptgrc_0_opp_val ** 2}` : `${hres}`}
		</p>
		<hr />
		<p>Opposite</p>
		<input type="number" bind:value={ptgrc_0_opp_val} />
		<p>Adjacent</p>
		<input type="number" bind:value={ptgrc_0_add_val} />
		<hr />
		<p>
			c^2 = √(a^2 + b^2) <br />
			c^2 = √({ptgrc_0_opp_val}^2 + {ptgrc_0_add_val}^2) <br />
			c^2 = √({ptgrc_0_opp_val ** 2} + {ptgrc_0_add_val ** 2}) <br />
			c^2 = √{ptgrc_0_opp_val ** 2 + ptgrc_0_add_val ** 2}
			{#if !hres.toString().match(/\./)}
				<br />
				c^2 = {Math.sqrt(ptgrc_0_opp_val ** 2 + ptgrc_0_add_val ** 2)}
			{:else}
				({Math.sqrt(ptgrc_0_opp_val ** 2 + ptgrc_0_add_val ** 2).toFixed(2)})
			{/if}
		</p>
	{:else}
		<p>
			{ehres.toString().match(/\./)
				? `√${ptgrc_1_hyp_val ** 2 - ptgrc_1_ehr_val ** 2}`
				: `${ehres}`}
		</p>
		<hr />
		<p>Hypotenuse</p>
		<input type="number" bind:value={ptgrc_1_hyp_val} />
		<p>Either Adjacent or Opposite</p>
		<input type="number" bind:value={ptgrc_1_ehr_val} />
	{/if}
</div>
<hr />
