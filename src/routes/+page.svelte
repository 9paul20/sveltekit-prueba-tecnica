<script lang="ts">
	import type { PageData } from './$types';

	export let data: PageData;

	$: ({ articles } = data);
</script>

<div class="grid">
	<div>
		<h2>Articles:</h2>
		{#each articles as article}
			<article>
				<header>{article.title}</header>
				<p>
					{article.content}
				</p>
				<form action="?/deleteArticle&id={article.id}" method="POST">
					<button type="submit" class="outline secondary">Delete Article</button>
				</form>
				<a href="/{article.id}" role="button" class="outline constrast" style="width: 100%;"
					>Edit Article</a
				>
			</article>
		{/each}
	</div>
	<form action="?/createArticle" method="POST">
		<h3>New Article</h3>
		<label for="title"> Title </label>
		<input type="text" id="title" name="title" />
		<label for="content"> Content </label>
		<textarea id="content" name="content" rows={5} />
		<button type="submit">Add Article</button>
	</form>
</div>
