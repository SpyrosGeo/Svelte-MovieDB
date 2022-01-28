<script context="module">
	export async function load({ fetch, params }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/discover/movie?api_key=${import.meta.env.VITE_API_KEY}&vote_average.gte=2.0&vote_average.lte=8.0&sort_by=vote_average.asc&include_adult=true`
		);
		const data = await res.json();
		if (res.ok) {
			return {
				props: {
					trashMovies: data.results
				}
			};
		}
	}
</script>

<script>
	import MovieDetails from '../components/MovieDetails.svelte';
	export let trashMovies;
	const getRandom = () => {
		let random = Math.floor(Math.random() * trashMovies.length);
		return trashMovies[random];
	};
	export let movie = getRandom();
    console.log(movie);
</script>

<MovieDetails {movie} />
