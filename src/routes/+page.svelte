<script lang="ts">
    import { config } from '../../moire.config';

    const themes = [
        'classic',
        'bento',
        'receipt',
        'pixel',
        'academic',
        'cyberpunk',
    ];
</script>

<div class="min-h-screen bg-white font-sans p-4 md:p-8">
    <header class="mb-12 text-center">
        <h1 class="text-4xl font-bold tracking-tight text-gray-900">
          <a href="https://docs.moire.blog" target="_blank" class="text-zinc-300 hover:bg-gray-100 transition-colors cursor-pointer bg-gray-50 px-2 rounded-lg">Moire</a>
          
          Themes</h1>
    </header>

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-x-8 gap-y-12 w-full max-w-[1920px] mx-auto">
        {#each themes as theme}
            <div class="flex flex-col h-[800px] group">
                <div class="flex items-center justify-between mb-3 px-1">
                    <h2 class="text-lg font-medium text-gray-900 capitalize tracking-tight">{theme}</h2>
                    <a 
                        href="/examples/{theme}" 
                        class="text-gray-400 hover:text-gray-900 transition-colors p-1"
                        target="_top"
                        title="Open {theme} in full screen"
                    >
                        <!-- External link icon -->
                        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="opacity-0 group-hover:opacity-100 transition-opacity"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/></svg>
                    </a>
                </div>
                
                <div class="flex-1 w-full relative border border-gray-100 rounded-lg overflow-hidden bg-gray-50">
                    <iframe 
                        src="/examples/{theme}" 
                        class="w-full h-full border-none"
                        title="{theme} theme preview"
                        loading="lazy"
                    ></iframe>
                </div>
            </div>
        {/each}
    </div>
    
    <footer class="mt-20 text-center text-gray-400 text-sm ">
         &copy; {new Date().getFullYear()} Moire
    </footer>
</div>
