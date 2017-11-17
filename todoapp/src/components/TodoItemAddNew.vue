<template>
  <li class='list__item'>
    <div class='list__item__check'>
      <div class='addnewbtn'
           v-on:click='addnew.visible = !addnew.visible'>{{ addnew.visible ? '-' : '+' }}</div>
    </div>

    <div class='list__item__info' v-show='addnew.visible'>
      <div class='title--edit'>
        <input type='text' v-model='addnew.title' placeholder='' />
      </div>
      <div class='description--edit'>
        <input type='text' v-model='addnew.description' placeholder='' />
      </div>
    </div>

    <div v-if='addnew.visible' class='list__item__action'>
      <div class='validatebtn' v-on:click='$emit("addNewTodo")'>ok</div>
    </div>
  </li>
</template>

<script>
  export default {
    name: 'TodoItemAddNew',
    props: ['addnew']
  }
</script>

<style scoped>
  .list__item {
    margin: 10px 0 10px 0;
    padding-bottom: 10px;
    border-bottom: 1px solid #333;
  }
  .list__item__check {
    display: inline-block;
    vertical-align: middle;
    text-align: center;
  }
  .list__item__check .addnewbtn {
    position: relative;
    width: 25px;
    height: 25px;
    border-radius: 4px;
    border: 1px solid #333;
    cursor: pointer;
    line-height: 26px;
    font-size: 26px;
  }
  .list__item__info {
    display: inline-block;
    vertical-align: middle;
    margin: 0 0 0 10px;
  }
  .list__item__action {
    display: inline-block;
    vertical-align: middle;
  }
  .list__item__action .validatebtn {
    position: relative;
    width: 25px;
    height: 25px;
    border-radius: 4px;
    border: 1px solid #333;
    line-height: 26px;
    text-align: center;
    cursor: pointer;
  }
</style>
