<script>
    export let todos;
</script>

<div class="mt-5">
    {#each todos as todo}
        <div
            class="flex items-center ps-4 border border-gray-200 rounded my-2 shadow-sm cursor-pointer hover:shadow-md py-4"
        >
            <input
                id={todo.id}
                type="checkbox"
                checked={todo.completed}
                value=""
                class="w-6 h-6 checkbox-teal text-teal-600 bg-gray-100 border-gray-300 rounded  focus:ring-teal-500 cursor-pointer"
            />
            <label
                for={todo.id}
                class="w-full ms-2 text-sm font-medium text-gray-900 cursor-pointer"
                >{todo.task}</label
            >
        </div>
    {:else}
        <h1>No tasks to do</h1>
    {/each}
</div>
