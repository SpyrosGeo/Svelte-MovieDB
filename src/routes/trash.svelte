<script context="module">
    
    const API="b66e2d221f89e3c5e7fcca745925733c"
    export async function load ({fetch,params}){
        const res = await fetch(`https://api.themoviedb.org/3/discover/movie?api_key=${API}&vote_average.gte=2.0&vote_average.lte=8.0&sort_by=vote_average.asc&include_adult=true`)
        const data = await res.json() 
        console.log(data.results)
        if(res.ok){
            return {
                props:{
                    trashMovies:data.results
                }
            }
        }
    }
</script>

<script>
    import MovieCard from "../components/MovieCard.svelte";
    export let trashMovies
    const getRandom = ()=>{
        let random = Math.floor(Math.random()*trashMovies.length)
        return trashMovies[random]
    }
</script>

<!-- <h3>Popular Movies</h3>
<div class="popular-movies">
	{#each trashMovies as trash}
		<MovieCard {trash} />
	{/each}
</div> -->