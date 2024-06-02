<script>
    import {createEventDispatcher} from 'svelte';
    const dispatcher = createEventDispatcher();

    let name;
    let beltColour;
    let age;
    const handleSubmit = () => {
        console.log(name, beltColour, age, skills);
        const person = {
            name, beltColour, age, skills, id: Math.random()
        }
        dispatcher('addPersonEvent', person);
    }
    let skills = [];

</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="Name" bind:value={name}/>
    <input type="number" placeholder="Age in years.." bind:value={age}/>
    <label>Skills:</label>
    <input type="checkbox" value="fighting" bind:group={skills}/>fighting<br/>
    <input type="checkbox" value="sneaking" bind:group={skills}/>sneaking<br/>
    <input type="checkbox" value="running" bind:group={skills}/>running<br/>
    <select bind:value={beltColour}>
        <option value="black">black</option>
        <option value="yellow">yellow</option>
        <option value="white">white</option>
        <option value="green">green</option>
        <option value="blue">blue</option>
     </select>

    <button>Add Person</button>
</form>
<style>

</style>

