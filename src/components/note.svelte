<h1 id={note.title}>{note.title}</h1>
<Card>
    <CardHeader style="justify-content: space-between;">
    <div style="display:flex;justify-content: flex-start;">
        {#if note.editing}
            <Button outline on:click={edit}>Finish</Button>
        {:else}
            <Button fill on:click={edit}>Edit</Button>
        {/if}

        <Button on:click={save}>Save</Button>
        <Button on:click={remove}>Delete</Button>

        {#if note.editingTitle}
            <Button outline on:click={changeTitle}>Finish</Button>
        {:else}
            <Button fill on:click={changeTitle}>Change Title</Button>
        {/if}

        <Button on:click={create}>Create</Button>
        <Button on:click={showHtml}>Html</Button>
    </div>
    
    <div>
        {#if note.editingTitle}
            <Input inputId="title" type="text" value={note.title}/>
        {:else}
            {note.title}
        {/if}
    </div>

    <div style="display:flex;justify-content: flex-end;">
        <Button>Save</Button>
        <Button>Refresh</Button>
    </div>
    </CardHeader>

    <CardContent>
        {#if note.editing}
            <TextEditor resizable value={note.value} bind:this={note.editor}/>
        {:else}
            {@html note.value}
        {/if}
    </CardContent>
    
    <CardFooter>
    <Link>Like</Link>
    <Link>Like</Link>
    <Link>Read more</Link>
    </CardFooter>
</Card>

<script>
    import {
        Link,
        Button,
        BlockHeader,
        TextEditor, Input,
        Card, CardContent, CardHeader, CardFooter
    } from 'framework7-svelte';

    export let note = {
        editing: false,
        editingTitle: false,
        title: "",
        value: "",
        editor: null
    };

    export let save = function()
    {
        console.log("not implemented");
    };

    export let removeNote = function()
    {
        console.log("not implemented");
    };

    export let createNote = function(title){
        console.log("not implemented");
    }  
    export let showHtml = function(){
        console.log("not implemented");
    }  

    function edit(v){
        note.editing = !note.editing;
        if (note.editing){

        }
        else{
        note.value = note.editor.instance().value;
        }
    }  

    function changeTitle(v){
        note.editingTitle = !note.editingTitle;
        if (note.editingTitle){

        }
        else{
        note.title = document.getElementById("title").value;
        }
    }  
    function create(){
        console.log("create");
        let title = window.getSelection().toString();
        if (title) createNote(title);
    }  
    function remove(){
        console.log("remove");
        removeNote();
    }  

</script>
