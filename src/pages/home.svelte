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
    }}}
    buttons={['bold', 'italic', 'hr']}
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

  <List>
    <ListInput type="textarea" label="Note" placeholder="Note" resizable/>
    <ListItem>
      {html}
    </ListItem>
  </List>


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
    TextEditor
  } from 'framework7-svelte';

  let html = "";

  function redraw(){
    console.log("redraw");
  }
</script>