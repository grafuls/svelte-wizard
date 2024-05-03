<!-- YOU CAN DELETE EVERYTHING IN THIS PAGE -->

<script>
	import { Stepper, Step } from '@skeletonlabs/skeleton';
	import { BsHddNetwork, BsPhone, BsHouses } from 'svelte-icons-pack/bs';
    import { Icon } from 'svelte-icons-pack';
	import Step1 from './Step1.svelte';
    import Step2 from './Step2.svelte';
    import Step3 from './Step3.svelte';
    import Step4 from './Step4.svelte';
    import Step5 from './Step5.svelte';

	/**
     * @type {number}
     */
	let group = 0;

	/**
     * @type {string[]}
     */
	let valueMultiple = [];

		
	const clientes = [{
		value: 0,
		label: 'Particular',
	}, {
		value: 1,
		label: 'Empresa',
	}, {
		value: 2,
		label: 'Autónomo',
	}]

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

</script>

<div class="container h-full mx-auto flex justify-center items-center">
	<div class="space-y-8 text-center">
		<div class="justify-center">
			<Stepper regionContent="space-y-8" stepTerm="Paso" buttonBackLabel="← Atras" buttonNextLabel="Siguiente →" buttonCompleteLabel="Confirmar">
				<Step>
					<svelte:fragment slot="header">Qué tipo de cliente eres?</svelte:fragment>
					<Step1 bind:group={group} clientes={clientes}></Step1>
				</Step>
				<Step>
					<svelte:fragment slot="header">En qué servicios estás interesado?</svelte:fragment>
					<Step2 bind:valueMultiple={valueMultiple} servicios={servicios} group={group}></Step2>
				</Step>
				<Step>
					<svelte:fragment slot="header">Qué uso tienes?</svelte:fragment>
					<Step3 bind:group={group} valueMultiple={valueMultiple} bind:servicios={servicios}></Step3>
				</Step>
				<Step>
					<svelte:fragment slot="header">Resumen</svelte:fragment>
					<Step4 bind:group={group} cliente={clientes[group].label} valueMultiple={valueMultiple} servicios={servicios}></Step4>
				</Step>
				<Step>
					<svelte:fragment slot="header">Contacto</svelte:fragment>
					<Step5></Step5>
				</Step>

			</Stepper>
		</div>
	</div>
</div>

<style lang="postcss">
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
