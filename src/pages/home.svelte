<Page name="home">
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
  <Card class="demo-card-header-pic">
      <CardHeader style="justify-content: space-between;">
        <div style="display:flex;justify-content: flex-start;">
          <Button>Save</Button>
          <Button>Save</Button>
        </div>
        <div>Note</div>
        <div style="display:flex;justify-content: flex-end;">
          <Button>Save</Button>
          <Button>Refresh</Button>
        </div>
      </CardHeader>

      <CardContent>
        {@html html}
      </CardContent>
      
      <CardFooter>
        <Link>Like</Link>
        <Link>Like</Link>
        <Link>Read more</Link>
      </CardFooter>
    </Card>


  <BlockTitle>Custom Button</BlockTitle>
  <BlockHeader>It is possible to create custom editor buttons. Here is the custom "hr" button that adds horizontal rule:</BlockHeader>
  <TextEditor resizable customButtons={{
    // property key is the button id
    hr: {
      // button html content
      content: '&lt;hr&gt;',
      // button click handler
      onClick(event, buttonEl) {
        document.execCommand('insertHorizontalRule', false);
      }
    },
    save: {
      // button html content
      content: 'Save',
      // button click handler
      onClick(event, buttonEl) {
        console.log("11111");
        save(event.value);
      }
    },    
    }}
    buttons={['bold', 'italic', 'hr', 'save']}
  />

  <Block strong>
    <Row>
      <Col>
        <Button fill on:click={redraw}>Redraw</Button>
      </Col>
      <Col>
        <Button fill>Button</Button>
      </Col>
      <Col>
        <Button fill round>Round</Button>
      </Col>
    </Row>
  </Block>

  <div >
    <div>
      {@html html}
    </div>
  </div>


  <BlockTitle>Navigation</BlockTitle>
  <List>
    <ListItem link="/about/" title="About"/>
    <ListItem link="/form/" title="Form"/>
  </List>

</Page>
<script>
  import {
    Page,
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
    ListInput,
    BlockHeader,
    TextEditor,
    Card, CardContent, CardHeader, CardFooter
  } from 'framework7-svelte';

  let html = "";

  function redraw(){
    console.log("redraw");
  }
  function save(v){
    html = v;
    console.log("save");
  }

</script>