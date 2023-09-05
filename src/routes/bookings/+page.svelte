<script lang="ts">
	import '../../app.postcss';
	import { page } from '$app/stores';
	$: activeUrl = $page.url.pathname;
</script>

