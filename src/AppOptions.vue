<script>
export default {
	data() {
		return {
			name: "Roger Ccopa",
			status: 'active',
			tasks: ['task one', 'task two', 'task three'],
			link: 'https://google.com'
		}
	}
}
</script>
<template>
	<h1>{{ name }}</h1>
	<br/>
	<p v-if="status === 'active'">User is active</p>
	<p v-else-if="status === 'pending'">user is pending</p>
	<p v-else>User Is INACTIVE</p>
	
	<ul>
		<li v-for="task in tasks" :key="task">{{task}}</li>
	</ul>
	<!-- <a v-bind:href="link">Go to Google</a> -->
	<a :href="link">Go to Google site</a>
</template>
