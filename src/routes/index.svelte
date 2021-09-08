<script lang="ts">
	import { createClient, defaultExchanges } from '@urql/core';
	import { setClient, query, operationStore } from '@urql/svelte';

	const client = createClient({
		url: 'https://0ufyz.sse.codesandbox.io',
		exchanges: [...defaultExchanges]
	});

	setClient(client);

	const todos = query(
		operationStore(`
  query {
    todos {
      id
      text
      complete
    }
  }
  `)
	);
</script>

{#if $todos.data}
	{JSON.stringify($todos.data)}
{/if}
