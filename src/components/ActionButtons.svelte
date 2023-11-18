<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    let checked = false;

    function onCheckAllTodos() {
        checked = !checked;
        dispatch("checkAllTodos", checked);
    }

    function onRemoveCompletedTodos() {
        dispatch("removeCompletedTodos");
    }
</script>

<div class="flex items-center mt-5" role="group">
    <button
        class="py-1 mr-2 font-small text-white bg-teal-700 rounded-lg border border-teal-700 hover:bg-teal-800 focus:ring-4 focus:outline-none focus:ring-teal-300 w-full"
        on:click={onCheckAllTodos}
    >
        {checked ? "Uncheck all" : "Check all"}
    </button>
    <button
        class="py-1 ms-2 font-small text-white bg-teal-700 rounded-lg border border-teal-700 hover:bg-teal-800 focus:ring-4 focus:outline-none focus:ring-teal-300 w-full"
        on:click={onRemoveCompletedTodos}
    >
        Remove completed
    </button>
</div>
