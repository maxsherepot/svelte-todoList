<script>
    import ActionButtons from "./components/ActionButtons.svelte";
    import AddTodoPanel from "./components/AddTodoPanel.svelte";
    import FilterPanel from "./components/FilterPanel.svelte";
    import TodoList from "./components/TodoList.svelte";

    let todos = [
        { id: 1, task: "some task 1", completed: false },
        { id: 2, task: "some task 2", completed: true },
        { id: 3, task: "some task 3", completed: false },
    ];

    let filter = "all";

    $: filterTodos = (filter) =>
        filter === "active"
            ? todos.filter((t) => !t.completed)
            : filter === "completed"
            ? todos.filter((t) => t.completed)
            : todos;

    $: filtered = filterTodos(filter);

    function onAddTodo(task) {
        const newTodo = {
            id: Date.now(),
            task,
            completed: false,
        };
        todos = [...todos, newTodo];
    }

    function onCheckAllTodos(checked) {
        todos = todos.map((t) => ({ ...t, completed: checked }));
    }

    function onRemoveCompletedTodos() {
        todos = todos.filter((t) => !t.completed);
    }
</script>

<div class="mx-auto mt-20 max-w-lg">
    <AddTodoPanel on:addTodo={(e) => onAddTodo(e.detail)} />
    <FilterPanel bind:filter />
    <TodoList bind:todos={filtered} />
    <hr class="mt-5" />
    <ActionButtons
        on:checkAllTodos={(e) => onCheckAllTodos(e.detail)}
        on:removeCompletedTodos={onRemoveCompletedTodos}
    />
</div>
