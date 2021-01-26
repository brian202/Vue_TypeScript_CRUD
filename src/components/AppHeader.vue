<template>
	<div class = "app-header">
		<h4>메모 어플리케이션</h4>
	</div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class AppHeader extends Vue {

}
</script>

<style scoped>
.app-header {
	overflow: hidden;
	padding: 52px 0 27px;
}
.app-header h4 {
	float: left;
	font-size: 24px;
	text-align: center;
}
</style>