<script context="module">
    const API="b66e2d221f89e3c5e7fcca745925733c"
    export async function load ({fetch}){
        const res = await fetch(`https://api.themoviedb.org/3/movie/popular?api_key=${API}`)
        const data = await res.json() 
        console.log(data);
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
    export let popular;
</script>

<h1>Hello there...</h1>