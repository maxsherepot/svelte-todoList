<script>
    export let todos;
    import { fade } from "svelte/transition";
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    let id;
    let hovered = false;
    let isInEditMode = false;
    let editedTask = "";

    function onTodoHover(todoId) {
        hovered = true;
        id = todoId;
    }

    function onEditTodo(todo) {
        const newTodo = { ...todo, task: editedTask };
        dispatch("onRenameTodo", newTodo);
        editedTask = "";
        isInEditMode = false;
    }
</script>

<div class="mt-5">
    {#each todos as todo (todo.id)}
        <div
            class="flex items-center px-4 border border-gray-200 rounded my-2 shadow-sm cursor-pointer hover:shadow-md py-3 justify-between flex-col"
            on:mouseenter={() => onTodoHover(todo.id)}
            on:mouseleave={() => (hovered = false)}
        >
            <div class="flex justify-between w-full">
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
                            class="py-1 px-3 mr-1 text-sm bg-light-700 rounded-lg border border-light-700 hover:bg-light-800 focus:ring-4 focus:outline-none focus:ring-light-300 w-full"
                            on:click={() => (isInEditMode = !isInEditMode)}
                        >
                            Edit
                        </button>
                        <button
                            class="py-1 px-3 ms-1 text-sm text-white bg-gray-700 rounded-lg border border-gray-700 hover:bg-gray-800 focus:ring-4 focus:outline-none focus:ring-gray-300 w-full"
                            on:click={() => dispatch("onRemoveTodo", todo.id)}
                        >
                            Delete
                        </button>
                    </div>
                {/if}
            </div>
            {#if isInEditMode && todo.id === id}
                <form
                    class="flex items-center w-full mt-4"
                    on:submit|preventDefault={() => onEditTodo(todo)}
                >
                    <input
                        type="text"
                        id="new-task"
                        class="bg-gray-50 border border-gray-300 text-gray-900 rounded-lg focus:ring-teal-500 focus:border-teal-500 block w-full p-2"
                        placeholder="Enter new task name"
                        bind:value={editedTask}
                    />
                    <button
                        type="submit"
                        class="inline-flex items-center py-1 px-5 ms-2 font-small text-white bg-purple-700 rounded-lg border border-purple-700 hover:bg-purple-800 focus:ring-4 focus:outline-none focus:ring-purple-300"
                        disabled={!editedTask}
                    >
                        Save
                    </button>
                </form>
            {/if}
        </div>
    {:else}
        <h1>No tasks to do</h1>
    {/each}
</div>
