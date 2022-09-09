<script>
import '../app.css'
import Nav from "../component/nav.svelte";

</script>

<main>
    <div class="p-8 max-w-6xl mx-auto">
        <Nav />
        <slot />
    </div>
</main>


