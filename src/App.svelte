<script>
  import logo from './assets/tasks_logo.png'

  let newToDo = '';
  let ToDoList = [
    {text: 'Fare la spesa', status: true},
    {text: 'Chiamare Andrea', status: false}
  ];
 
  function Add(){
    ToDoList = [...ToDoList, {text: newToDo, status: false}]
    newToDo = '';
    console.log(ToDoList);
  }
 
  function isEmpty(newToDo){ //disabling the button if the input is empty
    return newToDo == '';
  }
 
  function removeFromList(index) {
    ToDoList.splice(index, 1)
    ToDoList = ToDoList;
  }
</script>

<div>
  <img src={logo} class="logo" alt="Just Do It" />
</div>

<div>
  <input bind:value={newToDo} placeholder="Add an item" type="text">
  <button on:click={Add} disabled='{isEmpty(newToDo)}'>Add</button>
</div>

<div class="container">
  {#each ToDoList as element, index}
    <br />
    <div class="check">
      <input bind:checked={element.status} type="checkbox">
    </div>
    <div class="todo">
      <span class:done="{element.status}">{element.text}</span>
    </div>
    <div class="button-delete">
      <button class=delbutton on:click={() => removeFromList(index)}>DELETE</button>
    </div>
    <br />
  {/each}
</div>
 
<style>
  .check{
    box-sizing: border-box;
    border: 1px solid cyan;
    width: 10%;
    float:left;
  }  
  .container {
    border: 1px solid yellow;
  }
  .todo {
    box-sizing: border-box;
    border: 1px solid red;
    width: relative;
    float:left;
    text-align: left;
  }
  .button-delete {
    box-sizing: border-box;
    border: 1px solid green;
    width: relative;
    float: right;
  }
 
  .done {
    text-decoration: line-through;
    color: gray;
 
  }
  .delbutton {
    font-size: 10px;
    padding: 5px;
    color: crimson;
    background-color: rgb(24, 3, 6);
    float:left;
  }
  .logo {
    height: 6em;
    padding: 1.5em;
    margin-top: -100em;
    transition-duration: 700ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #4048ebaa);
    transition-duration: 200ms;
  }
  :disabled{
    opacity: 0.6;
    cursor: not-allowed;
    border-color: rgba(0, 0, 0, 0); 
  }
</style>