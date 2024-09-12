```vue
<script setup>
import { ref, onMounted } from "vue";

const name = ref("Francis");
const status = ref("active");
const items = ref(["Item 1", "Item 2", "Item 3"]);
const link = ref("www.google.com");
const newItem = ref("");

const toggleStatus = () => {
	if (status.value === "active") {
		status.value = "pending";
	} else if (status.value === "pending") {
		status.value = "inactive";
	} else {
		status.value = "active";
	}
};

const addNewItem = () => {
	if (newItem.value.trim() !== "") {
		items.value.push(newItem.value);
		newItem.value = "";
	}
};

const deleteTask = (index) => {
	items.value.splice(index, 1);
};

onMounted(async () => {
	try {
		const response = await fetch("https://jsonplaceholder.typicode.com/todos");
		const data = await response.json();
		items.value = data.map((item) => item.title);
	} catch (error) {
		console.log(`Error fetching: ${error}`);
	}
});

</script>
  
<template>
<h1>{{ name }}</h1>
<p v-if="status === 'active'">User is active</p>
<p v-else-if="status === 'pending'">User is pending</p>
<p v-else>User is inactive</p>

<form @submit.prevent="addNewItem">
	<label for="newItem">Add new task: </label>
	<input type="text" id="newItem" name="newItem" v-model="newItem" />
	<button type="submit">Submit</button>
</form>

<h3>My List</h3>
<ul>
	<li v-for="(item, index) in items" :key="item">
	<span>{{ item }}</span>
	<button @click="deleteTask(index)">x</button>
	</li>
</ul>

<!-- <a v-bind:href="link">Link to google</a> -->
<!-- Shorter way to write v-bind -->
<a :href="link">Link to google</a>

<!-- <button v-on:click="toggleStatus">Change status</button> -->
<!-- Shorter way to write v-on -->
<button @click="toggleStatus">Change status</button>

</template>
```