<script>
	export let data;
	let { supabase } = data;
	$: ({ supabase } = data);

	async function signIn() {
		await supabase.auth.signInWithOAuth({
			provider: 'google',
			options: {
				redirectTo: `http://example.com/auth/callback`
			}
		});
	}
</script>

{#if data.session}
	<p>Logged in as {data.session?.user.email}</p>
{:else}
	<p>Not logged in</p>
{/if}
<a href="/login">Go to login page</a>
