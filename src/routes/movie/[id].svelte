<script context="module">

    const API="b66e2d221f89e3c5e7fcca745925733c"
    //params to get movie.id from url
    export async function load({fetch,params}){
        const res = await fetch(`https://api.themoviedb.org/3/movie/${params.id}?api_key=${API}`)
        const data = await res.json() 
        console.log(data);
        if(res.ok){
            return {
                props:{
                    movie:data
                }
            }
        }
    }

</script>
<script>
    import MovieDetails from '../../components/MovieDetails.svelte'
    export let movie
</script>
<svelte:head>
    <title>{movie.title}</title>
</svelte:head>
<MovieDetails {movie}/>