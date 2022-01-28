<script context="module">
    const API="b66e2d221f89e3c5e7fcca745925733c"
    export async function load ({fetch}){
        const res = await fetch(`https://api.themoviedb.org/3/movie/popular?api_key=${API}`)
        const data = await res.json() 
        if(res.ok){
            return {
                props:{
                    popular:data.results
                }
            }
        }
    }
</script>
<script>
import SearchMovies from '../components/SearchMovies.svelte';

    import PopularMovies from '../components/PopularMovies.svelte'
    // import global from '../global.css'
    export let popular;

</script>
<section>
    <SearchMovies/>
    <PopularMovies {popular}/>
</section>

<style>
</style>