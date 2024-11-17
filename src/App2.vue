<script setup>
import { ref, onMounted } from 'vue';

const name = ref("Roger Ccopa Illapuma");
const status = ref("active");
const tasks = ref(["task one", "task two", "task 3"]);
const aNewTask = ref("");

const toggleStatus = () => {
	if (status.value === "active")
	{
		status.value = "pending";
	} else if (status.value === "pending")
	{
		status.value = "inactive";
	} else
	{
		status.value = "active";
	}
};

const addTask = () => {
	if (aNewTask.value.trim().length > 0) {
		tasks.value.push(aNewTask.value);
		aNewTask.value ="";
	}
}

const deleteTask = (index) => {
	tasks.value.splice(index, 1);
}

onMounted(async () => {
	try {
		const res = await fetch('https://jsonplaceholder.typicode.com/todos');
		const data = await res.json();
		tasks.value = data.map((task) => task.title);
	} catch(error) {
		console.log('Error fetching taks :', error);
	}
})
</script>

<template>
	<h1>{{ name }}</h1>
	<br />
	<p v-if="status === 'active'">User is active</p>
	<p v-else-if="status === 'pending'">user is pending</p>
	<p v-else>User Is INACTIVE</p>
	<br />

	<form @submit.prevent="addTask">
		<label for="newTask">Add Task </label>
		<input type="text" id="newTask" name="newTask" v-model="aNewTask">
		<button type="submit">Submit</button>
	</form>

	TASKS
	<ul>
		<li v-for="(task, index) in tasks" :key="task">
			<span>{{ task }}</span>
			<button @click="deleteTask(index)">X</button>
		</li>
	</ul>
	<br /><br />

	<button @click="toggleStatus()">
		Toggle Status
	</button>
</template>
