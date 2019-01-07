<template>
  <div id="todolist">
    <todo v-on:delete-todo="deleteTodo" v-for="todo in todos" v-bind:todo="todo">
    	
    </todo>
  </div>
</template>

<script type = "text/javascript" >
import Todo from './Todo';

export default { //此组件用于显示全部的todo列表
  props: ['todos'], //接收父组件传过来的值
  components: {
    Todo,
  },
  methods: {
  	//订阅子元素发布delete-todo的方法，
    deleteTodo(todo) {
      sweetalert({
        title: 'you sure about this?',
        text: 'You will remove this todo forever!',
        type: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#DD6B55',
        confirmButtonText: 'Yes, delete it!',
        closeOnConfirm: false,
      },
      () => {
        const todoIndex = this.todos.indexOf(todo);
        this.todos.splice(todoIndex, 1);
        sweetalert('Deleted!', 'Your To-Do has been deleted.', 'success');
      });
    },
    
    //完成创建
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
      sweetalert('Success!', 'To-Do completed!', 'success');
    },
  },
};
</script>

<style scoped>
p.tasks {
  text-align: center;
}
</style>
<style type="text/css">
	#todolist{
		border: 2px solid black;
	}
</style>

