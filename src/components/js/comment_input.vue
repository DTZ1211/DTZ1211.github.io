
<template>
		<div class='cinput'>
			<label>
				<span>用户名</span>
				<el-input
				  placeholder="请输入内容"
				  v-model="author"
				  clearable>
				</el-input>
			</label>
			<label>
				<span>评论内容</span>
				<el-input
				  type="textarea"
				  :rows="2"
				  placeholder="请输入内容"
				  v-model="content">
				</el-input>
			</label>
			<footer>
				<el-button type="primary" round @click='doSave'>发布</el-button>
			</footer>
		</div>
</template>


<script>
//评论模板主体组件
var commentInput = {
	data(){
		return {
			author: '',
			content: ''
		}
	},
	methods: {
		doSave(){
			if(!this.author){
				return this.$message('作者不能为空');
			}
			if(!this.content){
				return this.$message('内容不能为空');
			}
			
			//更新保存在localStorage里的作者名
			localStorage.setItem('vvv-authorname', this.author);
			
			//将请求发射出去
			this.$emit('woyaobaocun',{
				id: +new Date(),
				author: this.author,
				content: this.content
			});
			
			//clear
			this.content = '';
			
		}
	},
	created(){
		const authorname = localStorage.getItem('vvv-authorname');
		if(authorname){
			this.author = authorname;
		}
	}
};

//导出, default 代表默认导出, 一个模块中只能有一个
export default commentInput;

</script>

