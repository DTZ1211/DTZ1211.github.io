

<template>
		<div class='comment'>
			<span class='comment-author'>{{comment.author}}	:</span>
			<span class='comment-content'>{{comment.content}}</span>
			<el-tooltip class="item" effect="dark" content="删除" placement="right">
			<el-button class="el-icon-delete" style="margin-left:auto" @click="deleteMe" circle></el-button>
			</el-tooltip>
		</div>
</template>

<script>
export default{
	props: ['comment'],
	methods: {
		//删除评论
		deleteMe(){
			this.$emit('shanchuwo', this.comment.id);
		}
	}
};
</script>