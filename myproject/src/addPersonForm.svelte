<script>
    import { createEventDispatcher } from 'svelte';


    let dispatch = createEventDispatcher()
    let name;
    let beltColor;
    let age
    //bind converts numbers to integers

    let skills = [];


    const handlesubmit = () =>{
        const person = {
            name,
            beltColor,
            age,
            skills,
            id: Math.random()
        }

       

        dispatch('addPersonEvent', person)
    };

</script>




<form on:submit|preventDefault = {handlesubmit}>
    <input type="text" placeholder="name" bind:value={name}>
    <input type="text" placeholder="belt color" bind:value={beltColor}>
    <input type="number" placeholder="Age" bind:value={age}>


     <!-- svelte-ignore a11y-label-has-associated-control -->
     <label>Skills</label> 
    <input type="checkbox" bind:group={skills} value="fighting">fighting<br>
    <input type="checkbox" bind:group={skills} value="sneaking">sneaking<br>
    <input type="checkbox" bind:group={skills} value="running">running<br>

    <select bind:value={beltColor}>
        <option value="black">black</option>
        <option value="orange">Orange</option>
    </select>
    <button>Add Person</button>
</form>