<script>
    export let filter;
</script>

<div class="rounded-lg flex items-center mt-4" role="group">
    <button
        type="button"
        class="px-4 py-2 text-sm font-medium text-gray-900 border border-teal-600 rounded-s-lg hover:bg-gray-100 focus:text-teal-700 w-full"
        class:active={filter === "all"}
        on:click={() => (filter = "all")}
    >
        All
    </button>
    <button
        type="button"
        class="px-4 py-2 text-sm font-medium text-gray-900  border-t border-b border-teal-600 hover:bg-gray-100 focus:text-teal-700 w-full"
        class:active={filter === "active"}
        on:click={() => (filter = "active")}
    >
        Active
    </button>
    <button
        type="button"
        class="px-4 py-2 text-sm font-medium text-gray-900  border border-teal-600 rounded-e-lg hover:bg-gray-100 focus:text-teal-700 w-full"
        class:active={filter === "completed"}
        on:click={() => (filter = "completed")}
    >
        Completed
    </button>
</div>

<style>
    button.active {
        border: 3px solid rgb(15 118 110);
    }
</style>
