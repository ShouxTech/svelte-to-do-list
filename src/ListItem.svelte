<script>
	import { createEventDispatcher } from 'svelte';

    export let taskName = '';
    
	const dispatch = createEventDispatcher();

    function removeTask() {
        dispatch('removeTask', {
			taskName,
		});
    }
</script>

<div>
    <button on:click={removeTask}>X</button>
    <p>{taskName}</p>
</div>

<style>
    div {
        background-color: rgb(63, 113, 167);
        width: 100%;
        height: 32px;
        border-radius: 5px;
        text-align: center;
        position: relative;
        margin-bottom: 5px;
    }

    p {
        margin: 0;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        font-size: 14px;
    }

    button {
        display: block;
        position: absolute;
        background-color: rgb(63, 113, 167);
        border: none;
        border-radius: 5px;
        color: white;
        padding: 5px;
        cursor: pointer;
        top: 50%;
        transform: translate(0, -50%);
        margin-left: 2px;
    }
</style>