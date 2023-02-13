<script>
	import { each } from "svelte/internal";


    let tasks = [{text:'Walk dog', done:false},{text:'Walk cat', done:false},{text:'Walk friend', done:false}];
    function addTask(){
        tasks = tasks.concat({text:'', done:false});
    }
    function clearDoneTasks(){
        tasks = tasks.filter(v=>!v.done);
    }
</script>
<h1>TODO app</h1>

{#each tasks as {text,done}}
    <div class:done = {done}>
        <input type="checkbox" bind:checked={done}>
        <input bind:value={text}>
    </div>
{/each}
<button on:click={addTask}> Add task</button>
<button on:click={clearDoneTasks}> Clear completed</button>

<style>
    .done{
        opacity: .6;;
    }
</style>