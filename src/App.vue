<script>
export default {
	data() {
		return {
			name: "Roger Ccopa",
			status: false
		}
	}
}
</script>
<template>
	<h1>{{ name }}</h1>
	<br/>
	<p v-if="status">User is active</p> 
</template>
