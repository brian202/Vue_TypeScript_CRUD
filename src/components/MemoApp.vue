<!-- 메모들의 상태를 관리하는 컴포넌트 -->
<template>
	<div class = "memo-app">
		<memo-form @addMemo = 'addMemo'/>
		<ul class = 'memo-list'>
			<memo v-for = 'memo in memos'
						:key = 'memo.id'
						:memo = 'memo'/>
		</ul>
	</div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import MemoForm from '@/components/MemoForm.vue';
import Memo from '@/components/Memo.vue';

@Component({
	components: {
		Memo,
		MemoForm,
	}
})
export default class MemoApp extends Vue {
	memos = []

	created() {
		// 기존에 추가된 localStorgae 데이터가 있다면 created 훅에서 localStorage의 데이터를 컴포넌트 내의 memos에 
		// 넣어주고, 그렇지 않다면 그대로 빈 배열로 초기화
		this.memos = localStorage.memos ? JSON.parse(localStorage.memos) : [];
	}

	addMemo(payload: never) {
		//MemoForm에서 올려 받은 데이터를 먼저 컴포넌트 내부 데이터에 추가
		this.memos.push(payload);
		this.storeMemo();
	}

	storeMemo() {
		const memosToString = JSON.stringify(this.memos);
		localStorage.setItem('memos',memosToString);
	}

}
</script>

<style scoped>
	.memo-list {
		padding: 20px 0;
		margin: 0;
	}
</style>