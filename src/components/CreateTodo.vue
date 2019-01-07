<template>
  <div class='ui basic content center aligned segment' id="create-todo">
  	
    <button class='ui basic button icon' v-on:click="openForm" v-show="!isCreating">
      <i class='plus icon'></i> <!--加号图标,点击将v-show的值为false ,按钮消失-->
    </button>
    
 	<!--添加todo的列表，点击+之后可见-->
    <div class='ui centered card' v-show="isCreating">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>标题</label>
            <input v-model="titleText" type='text'>
          </div>
          <div class='field'>
            <label>详情</label>
            <input v-model="projectText" type='text'>
          </div>
          <div class='ui two button attached buttons'>
            <button class='ui basic blue button' v-on:click="sendForm()">添加</button>
            <button class='ui basic red button' v-on:click="closeForm">取消</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default { //此组件用于创造组件
  data() {
    return {
      titleText: '',
      projectText: '',
      isCreating: false,
    };
  },
  methods: {
  	//将按钮置为不可见，添加框可见
    openForm() {
      this.isCreating = true;
    },
    //取消添加，将按钮置为可见，添加框不可见
    closeForm() {
      this.isCreating = false;
    },
    
    //添加todo
    sendForm() {
      if (this.titleText.length > 0 && this.projectText.length > 0) {
        const title = this.titleText;
        const project= this.projectText;
        this.$emit('create-todo', {    //发布创建todo函数，并将title 和project的值传过去
          title,
         	project,
         	done: false,
        });
        this.titleText = '';
        this.projectText = '';
        this.isCreating = false; //恢复原来的样子
      }
    },
  },
};
</script>
<style type="text/css">
	#create-todo{
		background: #ccc;
	}
</style>
