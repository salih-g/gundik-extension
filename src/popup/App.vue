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

		<ul>
			<li>
				<h2>
					<a href="https://www.youtube.com/watch?v=kbU1KTCWLIc" target="_blank"
						>Bla bla</a
					>
				</h2>
				<!-- <link-prevue
					url="https://www.youtube.com/watch?v=kbU1KTCWLIc"
				></link-prevue> -->
			</li>
		</ul>
	</div>
</template>

<script>
import LinkPrevue from 'link-prevue';
export default {
	name: 'App',
	components: {
		LinkPrevue,
	},
};
</script>

<style>
html {
	width: 500px;
	height: 500px;

	padding: 0;
	margin: 0;

	background-color: #323234;
	color: #ededed;
}
* {
	box-sizing: border-box;
}

a {
	color: inherit;
	text-decoration: none;
}
a:hover {
	color: #4198d3;
}

li {
	list-style-type: none;
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

	background-color: #4198d3;
	color: white;

	border: none;
	border-radius: 5px;

	cursor: pointer;
}
.title {
	text-transform: capitalize;
}
</style>
