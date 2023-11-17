<script>
    import AddTodoPanel from "./components/AddTodoPanel.svelte";
    import TodoList from "./components/TodoList.svelte";

    let todos = [
        { id: 1, task: "some task 1", done: false },
        { id: 2, task: "some task 2", done: true },
        { id: 3, task: "some task 3", done: false },
    ];

    function onAddTodo(e) {
        const newTodo = {
            id: Date.now(),
            task: e.detail,
            done: false,
        };
        todos = [...todos, newTodo];
    }
</script>

<div class="mx-auto mt-20 max-w-lg">
    <AddTodoPanel on:addTodo={onAddTodo} />

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

    <TodoList {todos} />

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
