<script>
    import ActionButtons from "./components/ActionButtons.svelte";
    import AddTodoPanel from "./components/AddTodoPanel.svelte";
    import FilterPanel from "./components/FilterPanel.svelte";
    import TodoList from "./components/TodoList.svelte";

    let initialTodos = [
        { id: 1, task: "some task 1", completed: false },
        { id: 2, task: "some task 2", completed: true },
        { id: 3, task: "some task 3", completed: false },
    ];

    let filter = "all";

    const filterTodos = (filter, todos) =>
        filter === "active"
            ? todos.filter((t) => !t.completed)
            : filter === "completed"
            ? todos.filter((t) => t.completed)
            : todos;

    $: todos = filterTodos(filter, initialTodos);

    function onAddTodo(e) {
        const newTodo = {
            id: Date.now(),
            task: e.detail,
            completed: false,
        };
        initialTodos = [...todos, newTodo];
    }
</script>

<div class="mx-auto mt-20 max-w-lg">
    <AddTodoPanel on:addTodo={onAddTodo} />
    <FilterPanel bind:filter />
    <TodoList {todos} />
    <hr class="mt-5" />
    <ActionButtons />
</div>
