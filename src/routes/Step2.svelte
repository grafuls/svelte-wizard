
<script>
    import { ListBox, ListBoxItem } from '@skeletonlabs/skeleton';
    import { Icon } from 'svelte-icons-pack';

    /**
     * @type {number}
     */
    export let group;

    /**
     * @type {string[]}
     */
     export let valueMultiple;

     /**
     * @type {{ [x: string]: { name: any; }; }}
     */
     export let servicios;
</script>

<ListBox multiple>
    {#each Object.keys(servicios) as f}
        {#if group === 0 && f === 'centralita'}
        <span></span>
        {:else}
            <ListBoxItem regionDefault="text-left" bind:group={valueMultiple} name="medium" value={f}>
                <svelte:fragment slot="lead"><Icon src={servicios[f].icon} /></svelte:fragment>
                {servicios[f].name}
            </ListBoxItem>
        {/if}
    {/each}
</ListBox>
