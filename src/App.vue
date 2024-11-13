<script>
	export default {
		data() {
			return {
				name: "Roger Ccopa Illapuma",
				status: "active",
				tasks: ["task one", "task two", "task 3"],
				link: 'https://www.google.com',
			};
		},
		methods: {
			toggleStatus() {
				if (this.status === "active") {
					this.status = "pending";
				} else if (this.status === "pending") {
					this.status = "inactive";
				} else {
					this.active = "active";
				}
			}
		}
	};
</script>
<template>
	<h1>{{ name }}</h1>
	<br />
	<p v-if="status === 'active'">User is active</p>
	<p v-else-if="status === 'pending'">user is pending</p>
	<p v-else>User Is INACTIVE</p>

	TASKS
	<ul>
		<li v-for="task in tasks" :key="task">{{ task }}</li>
	</ul>
</template>
