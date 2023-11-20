<script>
    export let todos;
    import { fade } from "svelte/transition";

    //  let hovered = false;
    let hovered = false;
    let id;

    function onTodoHover(todoId) {
        hovered = true;
        id = todoId;
    }
</script>

<div class="mt-5">
    {#each todos as todo (todo.id)}
        <div
            class="flex items-center px-4 border border-gray-200 rounded my-2 shadow-sm cursor-pointer hover:shadow-md py-3 justify-between"
            on:mouseenter={() => onTodoHover(todo.id)}
            on:mouseleave={() => (hovered = false)}
        >
            <div class="flex items-center py-1">
                <input
                    id={todo.id}
                    type="checkbox"
                    checked={todo.completed}
                    value=""
                    class="w-6 h-6 checkbox-teal text-teal-600 bg-gray-100 border-gray-300 rounded  focus:ring-teal-500 cursor-pointer"
                    on:click={() => (todo.completed = !todo.completed)}
                />
                <label
                    for={todo.id}
                    class="w-full ms-2 font-medium text-gray-900 cursor-pointer"
                    >{todo.task}</label
                >
            </div>

            {#if hovered && todo.id === id}
                <div
                    class="flex items-center"
                    transition:fade={{ delay: 0, duration: 300 }}
                    role="group"
                >
                    <button
                        class="py-1 px-3 mr-1 text-sm text-white bg-yellow-700 rounded-lg border border-yellow-700 hover:bg-yellow-800 focus:ring-4 focus:outline-none focus:ring-yellow-300 w-full"
                    >
                        Edit
                    </button>
                    <button
                        class="py-1 px-3 ms-1 text-sm text-white bg-red-700 rounded-lg border border-red-700 hover:bg-red-800 focus:ring-4 focus:outline-none focus:ring-red-300 w-full"
                    >
                        Delete
                    </button>
                </div>
            {/if}
        </div>
    {:else}
        <h1>No tasks to do</h1>
    {/each}
</div>
