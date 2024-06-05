<script lang="ts">
	import { enhance } from '$app/forms';

	const authorizedExtensions = ['.jpg', '.jpeg', '.png', '.webp', '.exe'];
</script>

<form
	class="p-10 flex flex-col gap-5 justify-center items-center"
	method="post"
	use:enhance
	enctype="multipart/form-data"
>
	<div>
		<!-- <label for="file">Upload your file</label> -->
		<input
			type="file"
			id="file"
			name="fileToUpload"
			accept={authorizedExtensions.join(',')}
			required
		/>
	</div>

	<button class="btn variant-filled-primary" type="submit">Submit</button>
</form>
