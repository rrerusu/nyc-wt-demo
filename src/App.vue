<script setup>
import { ref } from 'vue';

let toxicityOutput = ref('');

async function sendText(content) {
	try {
		let request = await fetch("https://httpbin.org/post", {
			method: 'POST',
			content
		});
		// console.log(request.json());
		// this.toxicityOutput = await request.json();
		this.toxicityOutput = content;
		console.log(this.toxicityOutput);
		return request || [];
	} catch (error) {
			console.error(error);
	}
}
</script>

<template>
	<h3>{{toxicityOutput}}</h3>
	<input v-model="inputText">
	<button name="SubmitTextButton" type="button" @click="sendText(inputText)">Submit</button>
</template>