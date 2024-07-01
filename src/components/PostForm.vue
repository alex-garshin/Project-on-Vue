<template>
  <h4>Создание поста</h4>
  <form @submit.prevent class="form">
    <input
      v-model="post.title"
      @input="post.title = $event.target.value"
      class="input"
      type="text"
      placeholder="Название поста"
    />
    <input
      v-model="post.body"
      @input="post.body = $event.target.value"
      class="input"
      type="text"
      placeholder="Текст поста"
    />
    <button class="btn" @click="createPost">Создать</button>
  </form>
</template>
<script>
export default {
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit("create", this.post);
      this.post = {
        title: "",
        body: "",
      };
    },
  },
};
</script>
<style>
.input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 10px;
}

.btn {
  margin-top: 15px;
  padding: 10px 15px;
  align-self: flex-end;
  background: none;
  color: teal;
  border: 1px solid teal;
}
.form {
  display: flex;
  flex-direction: column;
}
</style>
