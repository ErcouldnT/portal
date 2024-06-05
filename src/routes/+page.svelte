<script lang="ts">
	import { enhance } from '$app/forms';
	import { FileDropzone } from '@skeletonlabs/skeleton';

	export let form;

	let files: FileList;

	function onChangeHandler(e: Event): void {
		console.log('File data:', e);
	}
</script>

<FileDropzone name="files" bind:files on:change={onChangeHandler}>
	<svelte:fragment slot="lead">Portal</svelte:fragment>
	<svelte:fragment slot="message"><strong>Upload a file</strong> or drag and drop</svelte:fragment>
	<svelte:fragment slot="meta">PNG, JPG, and GIF allowed.</svelte:fragment>
</FileDropzone>

<form use:enhance action="?/upload" method="POST" enctype="multipart/form-data">
	<input type="file" name="file" required />
	<button class="btn variant-filled-primary">Upload</button>

	{#if form}
		<p>Uploaded {form.uploaded}</p>
	{/if}
</form>
