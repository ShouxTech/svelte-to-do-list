<script>
    import ListItem from './ListItem.svelte';

    let tasks = [];

    function isWhitespace(data) {
        return data.trim().length == 0;
    }

    function textboxKeydown(e) {
        if (e.key !== 'Enter') return;

        const task = e.target.value;
        e.target.value = '';

        if (isWhitespace(task)) return;
        addTask(task);
    }

    function addTask(taskName) {
        /*tasks.push(taskName);
        tasks = tasks; // Trigger render update.*/

        tasks[tasks.length] = taskName; // Trigger render update.
    }

    function removeTask(name) {
        tasks = tasks.filter(task => task !== name);
    }
</script>

<div id="main">
    <input type="text" placeholder="Task" on:keydown="{textboxKeydown}">
    <div id="list">
        {#each tasks as task}
            <ListItem taskName={task} on:removeTask="{e => removeTask(e.detail.taskName)}"></ListItem>
        {/each}
    </div>
</div>

<style>
    #main {
        background-color: rgb(30, 58, 88);
        border-radius: 5px;
        border: 1px solid rgba(255, 255, 255, 0.5);
        width: 390px;
		height: 455px;
		position: absolute;
		top: 50%;
		left: 50%;
		margin: -250px 0 0 -200px;
    }

    input {
        text-align: center;
        width: 100%;
        border: 0;
        border-radius: 5px;
        padding: 0;
        margin: 0;
        height: 35px;
        background-color: rgb(60, 104, 151);
        color: white;
    }

    input::placeholder {
        color: rgb(181, 181, 181);
    }

    #list {
        width: 97.5%;
        height: 90%;
        margin-top: 5px;
        margin-left: 5px;
        background-color: rgb(13, 36, 61);
        border-radius: 5px;
        overflow-y: scroll;
    }
</style>