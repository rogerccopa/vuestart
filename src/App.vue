<script>
import {ref} from 'vue';

export default {
	setup() {
		const name = ref("Roger Ccopa Illapuma");
		const status = ref("active");
		const tasks = ref(["task one", "task two", "task 3"]);

		const toggleStatus = () => {
			if (status.value === "active") {
				status.value = "pending";
			} else if (status.value === "pending") {
				status.value = "inactive";
			} else {
				status.value = "active";
			}
		};

		return {
			name,
			status,
			tasks,
			toggleStatus
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
	<br />
	TASKS
	<ul>
		<li v-for="task in tasks" :key="task">{{ task }}</li>
	</ul>
	<br/><br/>

	<button @click="toggleStatus()">
		Toggle Status
	</button>
</template>
