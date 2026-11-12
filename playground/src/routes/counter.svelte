<h1>Click the Counter</h1>

<script lang="ts">
	import favicon from '#lib/assets/favicon.svg';
	import type { LayoutProps } from './$types';
    
    let count = $state(0);
    function increment() {
            count += 1;
        }
	
</script>

<button onclick={increment}>
	Clicks: {count}
</button>