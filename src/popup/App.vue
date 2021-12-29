<template>
	<div class="container">
		<h3 class="title">{{ mainTitle }}</h3>
		<form v-on:submit.prevent="createPost">
			<input
				class="input"
				type="text"
				placeholder="Başlık"
				v-model="newPost.title"
				required
			/>
			<br />
			<input
				class="input"
				type="url"
				placeholder="Link"
				v-model="newPost.url"
				required
			/>
			<br />
			<button class="addButton">Ekle</button>
		</form>

		<ul>
			<li v-for="(post, i) in posts" :key="i">
				<h2>
					<a :href="post.url" target="_blank">{{ post.title }}</a>
					<button class="deleteButton" @click="deletePost(post._id)">X</button>
				</h2>
				<!-- <link-prevue
					url="https://www.youtube.com/watch?v=kbU1KTCWLIc"
				></link-prevue> -->
			</li>
		</ul>
	</div>
</template>

<script>
import axios from 'axios';
import LinkPrevue from 'link-prevue';

export default {
	name: 'App',
	components: {
		LinkPrevue,
	},
	data() {
		return {
			mainTitle: 'İzleme Listesi',
			apiUrl: 'https://gundik.vercel.app/api/posts/',
			posts: {},
			newPost: {
				title: '',
				url: '',
			},
		};
	},
	methods: {
		async getPosts() {
			await axios
				.get(this.apiUrl)
				.then((r) => {
					this.posts = r.data.posts;
				})
				.catch((err) => {
					console.error(err);
				});
		},
		async createPost() {
			console.log('test');
			await axios.post(this.apiUrl, this.newPost).then((r) => {
				if (r.status == 200) {
					this.getPosts();
					this.mainTitle = 'İzleme Listesi';
				} else {
					this.mainTitle = 'Eklenemedi';
				}
			});
		},

		async deletePost(id) {},
	},
	async created() {
		await this.getPosts();
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
.title {
	text-transform: capitalize;
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
	color: #ededed;

	border: none;
	border-radius: 5px;

	cursor: pointer;
}

.deleteButton {
	margin-left: 10px;
	padding: 5px;

	font-size: 15px;
	background-color: #ed74ad;
	color: #ededed;

	border: none;
	border-radius: 2px;
	cursor: pointer;
}
</style>
