<script>
	import { createClient, setClient, operationStore, query } from '@urql/svelte';

  const client = createClient({
    url: "https://3eriodbh.api.sanity.io/v1/graphql/production/default",
  });

  setClient(client);

  const todos = operationStore(`
		query asdf {
			allProduct {
					_id
			}
		}
	`);

	query(todos);
</script>

<h1>chrstnfrrs manga list</h1>

{#if $todos.fetching}
  <p>Loading...</p>
{:else if $todos.error}
  <p>Oh no... {$todos.error.message}</p>
{:else}
  <ul>
    {#each $todos.data.allProduct as todo}
    <li>{todo._id}</li>
    {/each}
  </ul>
{/if}