<script lang="ts">
	import Mustache from 'mustache';
	import { onMount } from 'svelte';
	import data from './data.json';

	onMount(() => {
		const view = data;
		let mustacheTemplate: string = `
    <table>
      <tr>
        <th>Product</th>
        <th>Colour</th>
        <th>Price</th>
        <th>Buy</th>
      </tr>

      {{#product}}
      <tr>
        <td>{{name}}</td>
        <td>{{colour}}</td>
        <td>{{ price }}</td>
        {{#inStock}}<td><a href="buy.php?productId={{id}}">Buy Now!</a></td>{{/inStock}}
        {{^inStock}}<td>Out of Stock</td>{{/inStock}}
      </tr>
      {{/product}}
    </table>`;

		const output = Mustache.render(mustacheTemplate, view);
		document.getElementById('target').innerHTML = output;
	});
</script>

<!-- <svelte:head>
	<title>About</title>
	<meta name="description" content="About this app" />
</svelte:head> -->

<div class="text-column" id="target" />
