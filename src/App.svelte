<script>
  	import AddPersonForm from './AddPersonForm.svelte';

    import Modal from "./Modal.svelte";

	let showModal = false;

 	let firstName = 'Developer!!';
 	let lastName = 'Johan!!';
 	let belt = 'white';
 	let people = [
		{name: 'John Dow', belt: 'black', age: 25, id: 1},
		{name: 'Steven', belt: 'yellow', age: 45, id: 2},
		{name: 'Ioann', belt: 'blue', age: 28, id: 3}
 	]

 $: fullName = `${firstName} ${lastName}`;

 const changeBelt = () => {
	belt = belt === 'white' ? 'black' : 'white';
 }
 const handleInput = (e) => {
	belt = e.target.value;
 }
 const handleDelete = (id) => {
	people = people.filter((item) => item.id != id);
 }

 const toggleModal = () => {
	showModal = !showModal;
 }

 const addPerson = (e) => {
	console.log(e.detail);
	const newPerson = e.detail;
	people = [...people, newPerson];
 }
</script>

<Modal {showModal} on:click={toggleModal}>
<AddPersonForm on:addPersonEvent={addPerson}></AddPersonForm>
</Modal>
<main>
	<button on:click|once={toggleModal}>Show modal</button>
	<h2>{fullName} {belt} belt</h2>
	<input type="text" bind:value={belt}/>
	<input type="text" bind:value={firstName}/>
	<input type="text" bind:value={lastName}/>
	{#each people as person (person.id)}
	<div>
		<h>{person.name}</h> 
		<p>is {person.age} years old {person.belt} belt.</p>
		<button on:click={() => handleDelete(person.id)}>Delete</button>
	</div>
	{:else}
		<div>There are no people here...</div>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>