<template>
  <div>
    <form @submit.prevent>
      <h4><b>Создание поста</b></h4>
      <input
        class="input"
        type="text"
        placeholder="Название"
        v-bind:value="title"
        @input="title = $event.target.value"
      />
      <input
        class="input"
        type="text"
        placeholder="Описание"
        v-bind:value="body"
        @input="body = $event.target.value"
      />
      <button clas="btn" @click="createPost">Создать</button>
    </form>
    <div class="post" v-for="post in posts">
      <div><b>Заголовок:</b> {{ post.title }}</div>
      <div><b>Контент:</b> {{ post.body }}</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [
        { id: 1, title: "JS", body: "Something" },
        { id: 1, title: "JS 1", body: "Something" },
        { id: 1, title: "JS 2", body: "Something" },
      ],
      title: "a",
      body: "b",
    };
  },
  methods: {
    createPost() {
      const newPost = {
        id: Date.now(),
        title: this.title,
        body: this.body,
      };
      this.posts.push(newPost);
      this.title = "";
      this.body = "";
    },
    inputTitle(event) {
      this.title = event.target.value;
    },
  },
};
</script>

<style>
form {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 20px;
  background-color: white;
  border: 2px solid teal;
  border-radius: 20px;
  padding: 10px;
  background-color: bisque;
}

* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}

.post {
  margin-top: 15px;
  background-color: bisque;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  padding: 4px;
  border: solid 2px teal;
  margin: 12px;
}

.input {
  width: 400px;
  border: 1px solid teal;
  margin: 4px;
}

h4 {
  font-family: "Courier New", Courier, monospace;
}
</style>
