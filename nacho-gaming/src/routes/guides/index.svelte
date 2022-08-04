<script context='module'>
    export async function load({fetch}){
        //we could use this to fetch the data or destructure context above
        // context.fetch()
        const res = await fetch('https://jsonplaceholder.typicode.com/posts')
        const guides = await res.json()

        console.log(guides)
        //we return the json file as a prop
        if(res.ok){
            return{
                props:{guides}
            }
        }

        return{
            status: res.status,
            error: new Error('Could not fetch the guides')
        }
    }
</script>

<script>
    export let guides
</script>

<div class="guides">
    <ul>
        {#each guides as guide}
        <li>
            <a href="/">{guide.title}</a>
        </li>
        {/each}
    </ul>
</div>