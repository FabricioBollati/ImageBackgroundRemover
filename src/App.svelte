<script lang="ts">
  import StepUpload from './StepUpload.svelte'
  import Counter from "./lib/Counter.svelte";
  import { imageStatus } from './store';
  import { ImageStatus } from '../types.d';
  import StepEdit from './StepEdit.svelte';
</script>

<div
  class="max-w-xl m-auto  h-screen grid grid-cols-1 place-content-center   gap-x-2 font-semibold pt-10 p-4">
  <header class="flex justify-center py-10">
    <h1 class="text-3xl font-bold text-blue-900 tracking-tighter">
      Remove<span class="text-blue-600">Background</span>
    </h1>
  </header>
  <main class="w-fll block">
    {#if $imageStatus === ImageStatus.READY || $imageStatus === ImageStatus.UPLOADING}
    <StepUpload />
    {:else if $imageStatus === ImageStatus.DONE}
    <StepEdit />
    {/if}
  </main>
</div>
