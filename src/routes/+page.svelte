<script type="ts">
    import { type task } from "../lib/types";

    let taskObj: task
    let placeholderItem = ""

    function addItem () {
        if (placeholderItem != "") {
            taskObj.done[placeholderItem] = false
            taskObj.name[placeholderItem]
            taskObj = taskObj

            placeholderItem = ""
        }
    }

    function log () {
        console.log(taskObj)
    }

    // function handleKey (e) {
        // switch(e.keyCode) {
            // case 192:
            // addItem()
        // }
    // }
</script>

<h1 id="title">To Do:</h1>

<div class="list">
    Incomplete Items:

    <button class="wasteOfSpace"></button>

    {#if taskObj.done == false}
        {#each taskObj.name as taskName}
            <input bind:checked={taskObj.done[taskName]} type="checkbox"> {taskName}
        {/each}
    {/if}

    <!-- {#each Object.entries(taskObj) as [taskName, _value]} 
        {#if !taskObj[taskName]}
            <input bind:checked={taskObj[taskName]} type="checkbox"> {taskName}
        {/if}
    {/each} -->
</div>

<div id="allInputs">
    <input class="input" bind:value={placeholderItem}>

    <button class="input" on:click={addItem}>Add new task (or click `)</button>

    <button class="input" on:click={log}>console.log</button>
</div>  

<p class="list">
    Completed Items:

    <button class="wasteOfSpace"></button>

    {#if taskObj.done == true}
        {#each taskObj.name as taskName}
            <input bind:checked={taskObj.done[taskName]} type="checkbox"> {taskName}
        {/each}
    {/if}

    <!-- {#each Object.entries(taskObj) as [taskName, _value]}
        {#if taskObj[taskName]}
            <input bind:checked={taskObj[taskName]} type="checkbox"> {taskName}
        {/if}
    {/each} -->
</p>

<!-- <svelte:window on:keydown={handleKey} />  -->

<style>
    :global(body) {
        background-color: rgb(120, 141, 141);
        color: rgb(0, 0, 0);
    }

    #title {
        display: grid;
        place-content: center;
        font-size: 55px;
    }

    .input {
        border: 5px solid rgb(0, 0, 0);
        background-image: radial-gradient(#707070 25%,#FCFCFC);
        padding: 15px 0px;
        text-align: center;
        display: inline-grid;
        font-size: 20px;
        cursor: pointer;
        width: 90%;
        border-radius: 7px;
    }

    #allInputs {
        display: grid;
        grid-template-columns: auto auto auto;
        place-items: center;
        margin: 0px 15px;
    }

    .list {
        display: grid;
        grid-template-columns: max-content max-content;
        border: 5px solid rgb(0, 0, 0);
        background-image: radial-gradient(#707070 25%,#FCFCFC);
        padding: 15px;
        margin: 15px 40px;
        border-radius: 7px;
        width: 1385px;
        font-size: 20px;
        font-family: arial;
    }

    .wasteOfSpace {
        opacity: 0%;
    }
</style>