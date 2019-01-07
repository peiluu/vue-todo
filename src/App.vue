 <template>
  <div id="app">
    <h1 class="ui dividing centered header">TodoList</h1>
    <div class='ui three column centered grid'>
      <div class='column'>
      	 <!--v-bind:todos="todos"的作用是为了在父子组件间传值-->
        <todo-list v-bind:todos="todos"></todo-list>
        		<!--父组件订阅子组件发布的create-todo，并触发createTodo事件-->
        <create-todo v-on:create-todo="createTodo"></create-todo>
      </div>
    </div>
  </div>
</template>

<script>
import sweetalert from 'sweetalert'; //ui提示框架
import TodoList from './components/TodoList'; // 
import CreateTodo from './components/CreateTodo';

export default {
  name: 'app',
  components: {
  	//注册两个组件
    TodoList,
    CreateTodo,
  },
  data() {
    return {
      todos: [{
        title: '第一个 Todo',  //存在标题
        project:'我我我',      //存放具体项目
    
        done: false,        //表示没做
      }],
    };
  },
  methods: {
  	//接收传过来的参数并添加到todo里面，参数名字要一样
    createTodo(newTodo) {
      this.todos.push(newTodo);
       localStorage.setItem('list',JSON.stringify(this.list))
    },
  },
};
</script>
<style >
	#app{
		width: 60%;
		margin: 60px auto;
		border: 2px solid #CCCCCC;
	}

</style>
