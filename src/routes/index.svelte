<script>
  let asdf = {}
  fetch("https://3eriodbh.api.sanity.io/v1/graphql/production/default", {
    method: "POST",
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify({
      query: `
        query asdf {
          allProduct {
              _id
          }
        }
      `
    })
  })
  .then((res) => res.json())
  .then((result) => asdf=result);

</script>

<h1>chrstnfrrs manga list</h1>

{#if asdf.loading}
  <p>Loading...</p>
{:else if asdf.error}
  <p>Oh no... {asdf.error.message}</p>
{:else if asdf.data}
  <ul>
    {#each asdf.data.allProduct as qwer}
    <li>{qwer._id}</li>
    {/each}
  </ul>
{/if}