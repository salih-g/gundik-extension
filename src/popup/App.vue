<template>
	<div class="container">
		<h3 class="title">İzleme Listesi</h3>
		<form>
			<input class="input" type="text" placeholder="Baslik" required />
			<br />
			<input class="input" type="url" placeholder="Link" required />
			<br />
			<button class="addButton">Ekle</button>
		</form>
	</div>
</template>

<script>
export default {
	name: 'App',
	components: {},
};
</script>

<style>
html {
	width: 500px;
	height: 500px;

	background-color: #323234;
	color: #ededed;
}

.container {
	width: 80%;
	margin: 0 auto;
	text-align: center;
}
.input {
	width: 90%;
	height: 10px;
	border-radius: 5px;

	margin-bottom: 10px;
	padding: 10px;
}

.addButton {
	padding: 10px 30px;

	background-color: rgb(65, 152, 211);
	color: white;

	border: none;
	border-radius: 5px;

	cursor: pointer;
}
.title {
	text-transform: capitalize;
}
</style>
