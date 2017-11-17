<template>
  <li class='list__item'>

    <div class='list__item__check'
         v-bind:class="{ active: todo.checked }"
         v-on:click='$emit("checkTodo")'>
      <div class='checkbtn'></div>
    </div>

    <div class='list__item__info'>
      <div class='title--edit'
           v-if='todo.editMode'>
        <input
          type='text'
          v-model='todo.title'
          v-on:blur='todo.editMode = false'
          placeholder='todo.title' />
      </div>

      <div class='title--view'
           v-else
           v-on:click='todo.editMode = true'>
        {{ todo.title }}
      </div>

      <div class='description--view'>{{ todo.description }}</div>
    </div>

  </li>
</template>

<script>
  export default {
    name: 'TodoItem',
    props: ['todo']
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
  .list__item__check .checkbtn {
    position: relative;
    width: 25px;
    height: 25px;
    border-radius: 4px;
    border: 1px solid #333;
    cursor: pointer;
  }
  .list__item__check.active .checkbtn::after {
    content: 'L';
    position: absolute;
    top: -2px;
    left: 6px;
    transform: rotate(-135deg) scaleY(-1);
    font-size: 22px;
    font-weight: bold;
  }
  .list__item__info {
    display: inline-block;
    vertical-align: middle;
    margin: 0 0 0 10px;
  }
  .list__item__info .title--view {
    font-weight: bold;
    font-size: 16px;
  }
  .list__item__info .description--view {
    font-size: 14px;
  }
</style>
