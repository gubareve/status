<script>
	// @ts-nocheck

	import data from './status.json';
	const isOperational = data.services.every((service) => service.isOperational);
</script>

<div class="max-w-2xl mx-auto dark:text-white">
	<h1 class="text-4xl py-8 font-bold text-center dark:text-white">{data.config.appName} status</h1>
	<h2 class="text-2xl m-4 font-bold">Global status</h2>
	<div
		class={'m-4 p-4 text-black rounded-lg ' + (isOperational ? 'bg-green-400' : 'bg-orange-300')}
	>
		<div class="text-lg">
			{isOperational ? 'All systems operational' : 'Some systems degraded'}
		</div>
	</div>
	<h2 class="text-2xl m-4 pt-6 font-bold">Services</h2>
	<div
		class="grid grid-cols-1 divide-y dark:divide-gray-600 m-4 p-2 my-5 border-2 border-gray-200 dark:border-gray-600 rounded-lg"
	>
		{#each data.services as service}
			<div class="flex p-2">
				<div>{service.name}</div>
				<div class={'ml-auto ' + (service.isOperational ? 'text-green-700' : 'text-red-500')}>
					{service.isOperational ? 'Operational' : 'Degraded'}
				</div>
			</div>
		{/each}
	</div>
	<h2 class="text-2xl m-4 pt-6 font-bold">Maintenance</h2>
	{#if data.maintenance.show}
		<div class="bg-yellow-100 m-4 p-4 my-5 rounded-lg text-black">
			<h3 class="text-base">
				Upcoming maintenance - <b>{data.maintenance.time}</b>
			</h3>
			<h4 class="text-sm pt-5">
				{data.maintenance.message}
			</h4>
		</div>
	{/if}
	<h2 class="text-2xl m-4 pt-6 font-bold">Incidents</h2>
	<div class="m-4 p-2 my-5 border-2 border-gray-200 dark:border-gray-600 rounded-lg">
		<h3 class="text-base">
			{#if data.incidents.length > 0}
				Incident history
			{:else}
				No incidents reported
			{/if}
		</h3>
		<ul class="list-disc px-5 text-sm">
			{#each data.incidents as incident}
				<li><b>{incident.date}</b> {incident.description}</li>
			{/each}
		</ul>
	</div>
	<div class="text-center text-sm font-mono py-6">
		(c) {new Date().getFullYear()}
	</div>
</div>

<svelte:head>
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />
</svelte:head>

<style lang="postcss">
	:global(html) {
		font-family: 'Lato', Helvetica, Arial, sans-serif;
		background-color: theme(colors.white);
	}

	@media (prefers-color-scheme: dark) {
		:root {
			font-family: 'Lato', Helvetica, Arial, sans-serif;
			background-color: theme(colors.gray.900);
		}
	}
</style>
