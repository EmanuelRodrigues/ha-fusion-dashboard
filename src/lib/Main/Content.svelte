<script lang="ts">
	import { SHADOW_ITEM_MARKER_PROPERTY_NAME } from 'svelte-dnd-action';
	import Button from '$lib/Main/Button.svelte';
	import ConditionalMedia from '$lib/Main/ConditionalMedia.svelte';
	import Camera from '$lib/Main/Camera.svelte';
	import Configure from '$lib/Main/Configure.svelte';
	import Bar from '$lib/Sidebar/Bar.svelte';
	import Time from '$lib/Sidebar/Time.svelte';
	import Date from '$lib/Sidebar/Date.svelte';
	import Divider from '$lib/Sidebar/Divider.svelte';
	import Sensor from '$lib/Sidebar/Sensor.svelte';
	import Weather from '$lib/Sidebar/Weather.svelte';
	import Image from '$lib/Sidebar/Image.svelte';
	import WeatherForecast from '$lib/Sidebar/WeatherForecast.svelte';
	import Iframe from '$lib/Sidebar/Iframe.svelte';
	import History from '$lib/Sidebar/History.svelte';
	import Navigate from '$lib/Sidebar/Navigate.svelte';
	import Notifications from '$lib/Sidebar/Notifications.svelte';
	import Radial from '$lib/Sidebar/Radial.svelte';
	import Graph from '$lib/Sidebar/Graph.svelte';
	import Timer from '$lib/Sidebar/Timer.svelte';
	import Template from '$lib/Sidebar/Template.svelte';
	import { iconMapMeteocons } from '$lib/Weather';

	export let item: any;
	export let sectionName: string | undefined = undefined;
</script>

{#if item?.[SHADOW_ITEM_MARKER_PROPERTY_NAME] && item?.type === 'conditional_media'}
	<div class="shadow"></div>
{/if}

{#if item?.type === 'configure'}
	<Configure sel={item} />

{:else if item?.type === 'button'}
	<Button sel={item} {sectionName} />

{:else if item?.type === 'conditional_media'}
	<ConditionalMedia sel={item} />

{:else if item?.type === 'camera'}
	<Camera sel={item} responsive={false} muted={true} controls={false} />


{:else if item?.type === 'date'}
	<Date short_day={item.short_day} short_month={item.short_month} hide={item.hide} layout={item.layout}/>	

{:else if item?.type === 'divider'}
<Divider size={item.size} mode={item.mode} />	

{:else if item?.type === 'sensor'}
<Sensor entity_id={item.entity_id} prefix={item.prefix} suffix={item.suffix} date={item.date} />	

{:else if item?.type === 'weather'}
<Weather sel={item} />	

{:else if item?.type === 'weather_forecast'}
<WeatherForecast sel={item} />	

{:else if item?.type === 'image'}
<Image url={item.url} />	

{:else if item?.type === 'iframe'}
<Iframe url={item.url} size={item.size} preview={item.preview} />	

{:else if item?.type === 'history'}
<History entity_id={item.entity_id} period={item.period} />	

{:else if item?.type === 'navigate'}
<Navigate />	

{:else if item?.type === 'notifications'}
<Notifications sel={item} />	

{:else if item?.type === 'radial'}
<Radial entity_id={item.entity_id} name={item.name} strokeWidth={item.strokeWidth} />	

{:else if item?.type === 'time'}
<Time hour12={item.hour12} seconds={item.seconds} />	

{:else if item?.type === 'graph'}
<Graph entity_id={item.entity_id} name={item.name} period={item.period} stroke={item.stroke}   />	

{:else if item?.type === 'template'}
<Template sel={item} />	

{:else if item?.type === 'timer'}
<Timer sel={item} />	

{:else if item?.type === 'bar'}
	<Bar entity_id={item.entity_id} name={item.name} math={item.math} id={item.id}  />

{:else}
	<!-- if types are changed internally, don't break ui -->
	<Configure sel={{ id: item?.id }} />
{/if}

<style>
	.shadow {
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		visibility: visible;
		background: rgba(0, 0, 0, 0.125);
		margin: 0;
		border-radius: 0.65rem;
	}
</style>
