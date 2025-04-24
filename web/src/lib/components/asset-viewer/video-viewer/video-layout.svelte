<script lang="ts">
  import FullscreenButton from '$lib/components/asset-viewer/video-viewer/buttons/fullscreen-button.svelte';
  import MuteButton from '$lib/components/asset-viewer/video-viewer/buttons/mute-button.svelte';
  import PIPButton from '$lib/components/asset-viewer/video-viewer/buttons/pip-button.svelte';
  import PlayButton from '$lib/components/asset-viewer/video-viewer/buttons/play-button.svelte';
  import TimeGroup from './groups/time-group.svelte';
  import TimeSlider from './sliders/time-slider.svelte';
  import VolumeSlider from './sliders/volume-slider.svelte';
</script>

<media-gesture class="absolute inset-0 z-0 block h-full w-full" event="pointerup" action="toggle:paused"
></media-gesture>
<media-gesture class="absolute inset-0 z-0 block h-full w-full" event="dblpointerup" action="toggle:fullscreen"
></media-gesture>
<media-gesture class="absolute left-0 top-0 z-10 block h-full w-1/5" event="dblpointerup" action="seek:-10"
></media-gesture>
<media-gesture class="absolute right-0 top-0 z-10 block h-full w-1/5" event="dblpointerup" action="seek:10"
></media-gesture>

<div>
  <media-controls
    class="opacity-100 absolute inset-0 flex h-full w-full flex-col bg-gradient-to-t from-black/10 to-transparent transition-opacity"
  >
    <div class="flex-1"></div>
    <media-controls-group class="flex w-full items-center px-2 -mb-2">
      <TimeSlider></TimeSlider>
    </media-controls-group>
    <media-controls-group class="pl-1 pr-1 pb-2 flex w-full items-center">
      <PlayButton tooltipPlacement="top start" />
      <MuteButton tooltipPlacement="top start" />
      <VolumeSlider />
      <TimeGroup />
      <div class="flex-1"></div>

      <PIPButton tooltipPlacement="top"></PIPButton>
      <FullscreenButton tooltipPlacement="top end" />
    </media-controls-group>
  </media-controls>
</div>

<style scoped>
  media-controls {
    /* These CSS variables apply offsets to all tooltips/menus.  */
    --media-tooltip-y-offset: 30px;
    --media-menu-y-offset: 30px;
  }

  media-controls :global(media-volume-slider) {
    --media-slider-preview-offset: 30px;
  }
</style>
