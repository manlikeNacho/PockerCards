<script context="module">

   export async function load({params}){
        const id = params.id;
        // context.fetch()
        const res = await fetch(`https://pokeapi.co/api/v2/pokemon/${id}`)
        const pokeman = await res.json()

        if(res.ok){
            return{
                props:{pokeman}
            }
        }

        return{
            status: res.status,
            error: new Error('Could not fetch the pokeman')
        }
    }

</script>

<script>
    export let pokeman
    const type = pokeman.types[0].type.name
</script>
<div class="flex flex-col items-center">
    <h1 class="text-4xl text-center my-8 uppercase">{pokeman.name}</h1>
    <p>Type: <strong>{type}</strong> | Height: <strong>{pokeman.height}</strong> | Weight: <strong>{pokeman.weight}</strong></p>
    <img class="card-game" src={pokeman.sprites['front_default']} alt={pokeman.name} />
</div>