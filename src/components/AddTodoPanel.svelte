<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    let newTask = "";

    function onAddTodo() {
        dispatch("addTodo", newTask);
        newTask = "";
    }
</script>

<form class="flex items-center" on:submit|preventDefault={onAddTodo}>
    <input
        type="text"
        id="new-task"
        class="bg-gray-50 border border-gray-300 text-gray-900 rounded-lg focus:ring-teal-500 focus:border-teal-500 block w-full p-2"
        placeholder="Add new task"
        bind:value={newTask}
    />
    <button
        type="submit"
        class="inline-flex items-center py-2 px-5 ms-2 font-small text-white bg-teal-700 rounded-lg border border-teal-700 hover:bg-teal-800 focus:ring-4 focus:outline-none focus:ring-teal-300"
        disabled={!newTask}
    >
        Add
    </button>
</form>
