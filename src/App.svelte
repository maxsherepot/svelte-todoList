<script>
    const todos = [
        { id: 1, task: "some task 1", done: false },
        { id: 2, task: "some task 2", done: true },
        { id: 3, task: "some task 3", done: false },
    ];
</script>

<div class="mx-auto mt-20 max-w-lg">
    <!-- ADD NEW TODO -->
    <form class="flex items-center">
        <input
            type="text"
            id="new-task"
            class="bg-gray-50 border border-gray-300 text-gray-900 rounded-lg focus:ring-teal-500 focus:border-teal-500 block w-full p-2 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-teal-500 dark:focus:border-teal-500"
            placeholder="Add new task"
        />
        <button
            type="submit"
            class="inline-flex items-center py-2 px-5 ms-2 font-small text-white bg-teal-700 rounded-lg border border-teal-700 hover:bg-teal-800 focus:ring-4 focus:outline-none focus:ring-teal-300 dark:bg-teal-600 dark:hover:bg-teal-700 dark:focus:ring-teal-800"
        >
            Add
        </button>
    </form>

    <!-- FILTERS -->
    <div class="rounded-lg shadow flex items-center mt-4" role="group">
        <button
            type="button"
            class="px-4 py-2 text-sm font-medium text-gray-900 bg-white border border-gray-200 rounded-s-lg hover:bg-gray-100 hover:text-teal-700 focus:z-10 focus:ring-2 focus:ring-teal-700 focus:text-teal-700 dark:bg-gray-700 dark:border-gray-600 dark:text-white dark:hover:text-white dark:hover:bg-gray-600 dark:focus:ring-teal-500 dark:focus:text-white w-full"
        >
            All
        </button>
        <button
            type="button"
            class="px-4 py-2 text-sm font-medium text-gray-900 bg-white border-t border-b border-gray-200 hover:bg-gray-100 hover:text-teal-700 focus:z-10 focus:ring-2 focus:ring-teal-700 focus:text-teal-700 dark:bg-gray-700 dark:border-gray-600 dark:text-white dark:hover:text-white dark:hover:bg-gray-600 dark:focus:ring-teal-500 dark:focus:text-white w-full"
        >
            Active
        </button>
        <button
            type="button"
            class="px-4 py-2 text-sm font-medium text-gray-900 bg-white border border-gray-200 rounded-e-lg hover:bg-gray-100 hover:text-teal-700 focus:z-10 focus:ring-2 focus:ring-teal-700 focus:text-teal-700 dark:bg-gray-700 dark:border-gray-600 dark:text-white dark:hover:text-white dark:hover:bg-gray-600 dark:focus:ring-teal-500 dark:focus:text-white w-full"
        >
            Completed
        </button>
    </div>

    <!-- TODOS LIST -->
    <div class="mt-5">
        {#each todos as todo}
            <div
                class="flex items-center ps-4 border border-gray-200 rounded dark:border-gray-700 my-2 shadow-sm"
            >
                <input
                    id={todo.task}
                    type="checkbox"
                    value=""
                    class="w-6 h-6 checkbox-teal text-teal-600 bg-gray-100 border-gray-300 rounded dark:ring-offset-gray-800 dark:bg-gray-700 dark:border-gray-600 focus:ring-teal-500"
                />

                <label
                    for={todo.task}
                    class="w-full py-4 ms-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                    >{todo.task}</label
                >
            </div>
        {:else}
            <h1>No tasks to do</h1>
        {/each}
    </div>

    <hr class="mt-5" />

    <!-- ACTION BTNS -->
    <div class="flex items-center mt-5" role="group">
        <button
            class="py-1 mr-2 font-small text-white bg-teal-700 rounded-lg border border-teal-700 hover:bg-teal-800 focus:ring-4 focus:outline-none focus:ring-teal-300 dark:bg-teal-600 dark:hover:bg-teal-700 dark:focus:ring-teal-800 w-full"
        >
            Check all
        </button>
        <button
            class="py-1 ms-2 font-small text-white bg-teal-700 rounded-lg border border-teal-700 hover:bg-teal-800 focus:ring-4 focus:outline-none focus:ring-teal-300 dark:bg-teal-600 dark:hover:bg-teal-700 dark:focus:ring-teal-800 w-full"
        >
            Remove completed
        </button>
    </div>
</div>
