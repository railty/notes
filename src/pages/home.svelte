<Page bgColor="gray" name="home">
  <!-- Top Navbar -->
  <Navbar large sliding={false}>
    <NavLeft>
      <Link iconIos="f7:menu" iconAurora="f7:menu" iconMd="material:menu" panelOpen="left" />
    </NavLeft>
    <NavTitle sliding>notes</NavTitle>
    <NavRight>
      <Link iconIos="f7:menu" iconAurora="f7:menu" iconMd="material:menu" panelOpen="right" />
    </NavRight>
    <NavTitleLarge>notes</NavTitleLarge>
  </Navbar>

  <BlockTitle>Card</BlockTitle>

  <Link href="#555" animate={true} ignoreCache={true} on:click={onclick}>555</Link>

  {#each notes as note, idx}  
    <Note 
      bind:note={note} 
      save={save} 
      createNote={(title)=>{createNote(title, idx)}} 
      removeNote={(e)=>{removeNote(idx)}}
      showHtml={(e)=>{showHtml(idx)}}
    />
  {/each}

  <Popup bind:this={popup}>
    <Page>
      <Card>
        <CardContent>
          <BlockTitle>Title</BlockTitle>
            <Input type="textarea" value={html} />
        </CardContent>
        <CardFooter>
          <Button on:click={closePopup}>OK</Button>
          <Button on:click={closePopup}>Cancel</Button>
        </CardFooter>
      </Card>
    </Page>
  </Popup>
</Page>


<script>
  import { onMount } from 'svelte';
  import {
    f7, 
    Page, Popup,
    Navbar,
    NavLeft,
    NavTitle,
    NavTitleLarge,
    NavRight,
    Link,
    Toolbar,
    Block,
    BlockTitle,
    List,
    ListItem,
    Row,
    Col,
    Button,
    ListInput, Input,
    BlockHeader,
    TextEditor,
    Card, CardContent, CardHeader, CardFooter
  } from 'framework7-svelte';

  import Note from "../components/note.svelte";
  let popup;

  let notes = [{
    editing: false,
    title: "Home",
    value: "",
    editor: null
  }, {
    editing: false,
    value: "",
    editor: null
  }, {
    editing: false,
    value: "",
    editor: null
  }, {
    editing: false,
    value: "",
    editor: null
  },
  ];

  function save(){
    console.log("save");
    f7.form.storeFormData("#notes", notes);
  }

  function load(){
    notes = f7.form.getFormData("#notes");
    console.log(notes);
  }

	onMount(async () => {
    console.log("onmount");
		load();
  });    
  
  function openPopup(){
    popup.open(true);
  }

  function closePopup(){
    popup.close(true);
  }

  function removeNote(idx){
    console.log(idx);
    notes = [...notes.slice(0,idx), ...notes.slice(idx+1, notes.length)];
  }

  function createNote(title, idx){
    //console.log(title);
    //console.log(idx);

    notes = [...notes.slice(0,idx), {
      editing: false,
      title: title,
      value: "",
      editor: null
    }, ...notes.slice(idx, notes.length)];
  }

  let html;
  function showHtml(idx){
    console.log(notes[idx].value);
    html = notes[idx].value;
    popup.open(true);
  }


function onclick(event) 
{
  event.preventDefault();
  let o = document.getElementById("555");
  o.scrollIntoView({behavior: "smooth", block: "start", inline: "nearest"});

}

</script>