<script>
	import Modal from './Modal.svelte'

	let people = [
		{ name: 'yoshi', beltColour: 'black', age: 25, id: 1 },
		{ name: 'mario', beltColour: 'orange', age: 45, id: 2 },
		{ name: 'luigi', beltColour: 'brown', age: 35, id: 3 }
  	];	

	const handleClick = (e, id) => {
		// delete the person from people
		people = people.filter((person) => person.id != id)
	}

	let num = 5

</script>

<Modal />
<main>
	{#each people as person (person.id)}
		<div>
			<h4>{person.name}</h4>
			{#if person.beltColour === 'black'}
				<p>
					<strong>Master Ninja</strong>
				</p>
			{/if}
			<p>{person.age} years old, {person.beltColour} belt.</p>
			<button on:click={(e) => 
				handleClick(e, person.id)
			}>Delete</button>
		</div>
	{:else}
		<p>There are no people to show...</p>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>