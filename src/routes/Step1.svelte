<script>
// @ts-nocheck

	import { RadioGroup, RadioItem } from '@skeletonlabs/skeleton';

	/**
     * @type {number}
     */
     export let group;
	/**
     * @type { value: number; label: string; }[]
     */
	export let clientes;
</script>

	
<RadioGroup rounded="rounded-container-token" flexDirection="flex-col">
    {#each clientes as cliente}
    <RadioItem bind:group={group} name="justify" value={cliente.value}>{cliente.label}</RadioItem>
    {/each}
</RadioGroup>