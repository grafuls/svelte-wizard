<!-- YOU CAN DELETE EVERYTHING IN THIS PAGE -->

<script>
	import { Stepper, Step } from '@skeletonlabs/skeleton';
	import { RadioGroup, RadioItem } from '@skeletonlabs/skeleton';
	import { BsCheck, BsHddNetwork, BsPhone, BsHouses } from 'svelte-icons-pack/bs';
    import { Icon } from 'svelte-icons-pack';
	import { ListBox, ListBoxItem } from '@skeletonlabs/skeleton';
	let group = 0;

	const fibras = [{
		value: 1,
		label: '300MB',
	}, {
		value: 2,
		label: '500MB',
	}, {
		value: 3,
		label: '1000MB',
	}]

		
	const moviles = [{
		value: 1,
		label: 'Datos Ilimitados',
	}, {
		value: 2,
		label: '20GB',
	}, {
		value: 3,
		label: '5GB',
	}]

			
	const centrales = [{
		value: 1,
		label: 'Avanzados',
	}, {
		value: 2,
		label: 'Básicos',
	}, {
		value: 3,
		label: 'Inalámbricos',
	}]

	let servicios = {
		fibra: {name: 'Fibra Óptica', selected: false, values: fibras, icon: BsHddNetwork, selectedValue: 1},
		moviles: {name: 'Líneas Móviles', selected: false, values: moviles, icon: BsPhone, selectedValue: 1},
		centralita: {name: 'Centralita Virtual', selected: false, values: centrales, icon: BsHouses, selectedValue: 1}
	};

	let valueMultiple = [];


	function toggle(flavor) {
		servicios[flavor].selected = !servicios[flavor].selected;
	}


</script>

<div class="container h-full mx-auto flex justify-center items-center">
	<div class="space-y-10 text-center flex flex-col items-center">
		<div class="flex justify-center space-x-2">
			<Stepper stepTerm="Paso" buttonBackLabel="← Atras" buttonNextLabel="Siguiente →" buttonCompleteLabel="Confirmar">
				<Step>
					<svelte:fragment slot="header">Qué tipo de cliente eres?</svelte:fragment>
	
					<RadioGroup rounded="rounded-container-token" flexDirection="flex-col">
						<RadioItem bind:group={group} name="justify" value={0}>Particular</RadioItem>
						<RadioItem bind:group={group} name="justify" value={1}>Empresa</RadioItem>
						<RadioItem bind:group={group} name="justify" value={2}>Autónomo</RadioItem>
					</RadioGroup>
	
				</Step>
				<Step>
					<svelte:fragment slot="header">En qué servicios estás interesado?</svelte:fragment>
					
					<!-- {#each Object.keys(servicios) as f}
					<div class="flex justify-center space-x-2">
						<button
							class="chip {servicios[f] ? 'variant-filled' : 'variant-soft'}"
							on:click={() => { toggle(f); }}
							on:keypress
						>
							{#if servicios[f]}<span><Icon src={BsCheck} /></span>{/if}
							<span class="capitalize">{f}</span>
						</button>
					</div>
					{/each} -->

					<ListBox multiple>
					{#each Object.keys(servicios) as f}
					{#if group === 0 && f === 'centralita'}
					<span></span>
					{:else}
						<ListBoxItem bind:group={valueMultiple} name="medium" value={f}>{servicios[f].name}</ListBoxItem>
					{/if}
					{/each}
					</ListBox>

				</Step>
				<Step>
					<svelte:fragment slot="header">Qué uso tienes?</svelte:fragment>
					{#each valueMultiple as f}
					<div class="flex justify-center space-x-2">
						<span>{servicios[f].name}</span>
						<RadioGroup>
							{#each servicios[f].values as v}
							<RadioItem bind:group={servicios[f].selectedValue} name={f} value={v.value}>{v.label}</RadioItem>
							{/each}
						</RadioGroup>
					</div>
					{/each}
				</Step>
				<Step>
					<svelte:fragment slot="header">Resumen</svelte:fragment>
				</Step>
				<Step>
					<svelte:fragment slot="header">Contacto</svelte:fragment>
				</Step>

			</Stepper>
		</div>
	</div>
</div>

<style lang="postcss">
	figure {
		@apply flex relative flex-col;
	}
	figure svg,
	.img-bg {
		@apply w-64 h-64 md:w-80 md:h-80;
	}
	.img-bg {
		@apply absolute z-[-1] rounded-full blur-[50px] transition-all;
		animation: pulse 5s cubic-bezier(0, 0, 0, 0.5) infinite,
			glow 5s linear infinite;
	}
	@keyframes glow {
		0% {
			@apply bg-primary-400/50;
		}
		33% {
			@apply bg-secondary-400/50;
		}
		66% {
			@apply bg-tertiary-400/50;
		}
		100% {
			@apply bg-primary-400/50;
		}
	}
	@keyframes pulse {
		50% {
			transform: scale(1.5);
		}
	}
</style>
