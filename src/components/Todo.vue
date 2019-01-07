<template>
  <div class='ui centered card' id="todo">
    <div class="content" v-show="!isEditing">
      <div class='header'>
          {{ todo.title }} <input type="checkbox" class="mint-checkbox">
      </div>
      <div class='meta'>
          {{ todo.project }}
      </div>
      <div class='extra content'>
      	<!--//重新编辑已经添加好的todo-->
          <span class='right floated edit icon' v-on:click="showForm">
          <i class='edit icon'></i>
        </span>
        <span class='left floated trash icon' v-on:click="deleteTodo(todo)">
          <i class='trash icon'></i>
        </span>
      </div>
    </div>
    <div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label>Title</label>
          <input type='text' v-model="todo.title" >
        </div>
        <div class='field'>
          <label>Project</label>
          <input type='text' v-model="todo.project" >
        </div>
        <div class='ui two button attached buttons'>
          <button class="ui teal button" v-on:click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script type="text/javascript">
  export default {       //此组件用来写当前组件
    props: ['todo'],
    data() {
      return {
        isEditing: false,  //
      };
    },
    methods: {
      completeTodo(todo) {
      	//发布一个函数给父组件
        this.$emit('complete-todo', todo);     
      },
      deleteTodo(todo) {
        this.$emit('delete-todo', todo);
      },
      showForm() {
        this.isEditing = true;
      },
      hideForm() {
        this.isEditing = false;
      },
    },
  };
</script>
<style type="text/css">
	#todo{
		background: forestgreen;
	}
</style>
