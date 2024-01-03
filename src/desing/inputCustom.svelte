<script>
    export let control = 'textarea'
    export let value 
    export let type = 'text'
    export let nombre 
    export let id
    export let placeholder
</script>

<div class="form-group">
    <label {id} class="block mb-2 text-sm font-medium text-gray-900 dark:text-black">{nombre}</label>
    {#if control === 'textarea'}
    <textarea {id} {placeholder} {value} on:input rows="4" class="block p-2.5 w-1/4 text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"></textarea>
    {:else}
    <input {type} {id} {placeholder} {value} on:input required class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-1/4 p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
    {/if}
    
</div>