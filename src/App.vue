<script setup>
async function sendText(content) {
	try {
		let request = await fetch("https://httpbin.org/post", {
			method: 'POST',
			content
		});
		document.getElementById('toxicityOutput').value = request.body;
		// console.log(request);
		return request || [];
	} catch (error) {
			console.error(error);
	}
}
</script>

<template>
  <h3 id="demo">Test</h3>

  <form>
    <input id="inputText" name="inputText">
    <button name="SubmitTextButton" type="button" onclick="sendText(document.getElementById('inputText').value)">Submit</button>
    <p id="toxicityOutput"></p>
  </form>
</template>