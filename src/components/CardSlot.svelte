<!-- with html being sent as a child, use the slot keyword  -->
<!-- <div><slot/></div> -->
<!-- If you want default content you can put it as a child of the slot  -->
<div><slot>Here is the default content</slot></div>
<style>
    div{
        margin: 20px;
        padding: 20px;
        box-shadow: 0 4px 8px 0;
        width: 200px;
    }
</style>