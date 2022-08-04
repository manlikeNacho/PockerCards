<script>
	import Modal from './modal.svelte'
	import AddPersonForm from './addPersonForm.svelte'

	let showModal = false;

	// export let name;
	// let lastName = 'Nacho'
	// let firstName ='sins'
	
	// $: fullName = `${lastName} ${firstName}`;
	// $: console.log(fullName)
	// const hnadleClick = ( )=>{
	// 	lastName = 'sins'
	// }

	// const handleInput = (e) => {
	// 	lastName = e.target.value
	// };

	const toggleModal = () =>{
		showModal = !showModal;
	}

	let people = [
		{name:'yoshi', beltColor:'black',age:25, id:1},
		{name:'mario', beltColor:'orange',age:45, id:2},
		{name:'luigi', beltColor:'orange',age:35, id:3}
	]

	const handleClick = (id) =>{
		//delete the Person
		people = people.filter((person) => person.id != id);
	}


	const addPerson= (e)=>{
		console.log(e.detail)
	}
</script>





<Modal message='Hey, I am a prop value' isPromo={true} {showModal} on:click={toggleModal} >
	<AddPersonForm on:addPerson={addPerson}/>
</Modal>
<main>
	<!-- <h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<h3>Hello {fullName}</h3>
	<button on:click={hnadleClick}>update belt color</button> -->
	<!-- <input type="text" on:input={handleInput} value={lastName}/> -->
	<!-- <input type="text" bind:value={lastName}>
	<input type="text" bind:value={firstName}> -->

    <button on:click={toggleModal}>Open Modal</button>
	{#each people as person (person.id)}
	<div>
		<h4>{person.name}</h4>
		{#if person.beltColor === 'black'}
		<p><strong>Master Ninja</strong></p>
		{/if}
		<p>{person.age} years old, {person.beltColor} belt.</p>
		<button on:click={(e)=> {handleClick(person.id)}}>delete</button>
	</div>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	/* h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	} */

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>