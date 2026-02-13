<script lang="ts">
    import { page } from '$app/stores';
    import { config } from '../../../../moire.config';
    import type { PageData } from './$types';

    let { data }: { data: PageData } = $props();
    let ThemeComponent = $state<any>(null);

    let theme = $derived($page.params.theme);

    $effect(() => {
        document.body.className = theme;
        return () => {
            document.body.className = '';
        };
    });

    // Dynamic import based on the theme parameter
    $effect(() => {
        let loader: () => Promise<any>;
        if (theme === 'receipt') {
            loader = () => import('$themes/receipt/index.svelte');
        } else if (theme === 'cyberpunk') {
            loader = () => import('$themes/cyberpunk/index.svelte');
        } else if (theme === 'academic') {
            loader = () => import('$themes/academic/index.svelte');
        } else if (theme === 'bento') {
            loader = () => import('$themes/bento/index.svelte');
        } else if (theme === 'pixel') {
            loader = () => import('$themes/pixel/index.svelte');
        } else if (theme === 'classic') {
            loader = () => import('$themes/classic/index.svelte');
        } else {
             // Fallback or 404 handling could go here, for now default to classic
            loader = () => import('$themes/classic/index.svelte');
        }

        loader().then(module => {
            ThemeComponent = module.default;
        });
    });
</script>

{#if ThemeComponent}
    <ThemeComponent {data} {config} />
{:else}
    <div class="min-h-screen flex items-center justify-center">Loading theme: {theme}...</div>
{/if}
