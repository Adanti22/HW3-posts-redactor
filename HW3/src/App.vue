<script>
/* Создать редактор постов на вью,который состоит из 4 компонентов: главный, компонент создания поста,компонент список постов и компонент для отображения каждого отдельного поста в списке,использовать все полученные знания: директивы,обмен данными между компонентами, стилизация компонентов.Дополнительно: реализовать оформление каждого поста в виде: выбора цвета фона,цвета шрифта, размера шрифта.
 */

import CreatePost from "./components/Create-post.vue";
import ListOfPosts from "./components/List-of-posts.vue";
import ShowPost from "./components/ShowPost.vue";
export default {
  data() {
    return {
      posts: [],
      post: {},
      current: 0,
    };
  },
  components: {
    CreatePost,
    ListOfPosts,
    ShowPost,
  },
  methods: {
    push(post) {
      const newPost = { ...post };
      this.posts.push(newPost);
      console.log(this.posts);
    },
    newCurrent(currPost) {
      this.post = currPost;
      this.current = currPost.id;
    },
  },
  mounted() {
    alert("Для изменения параметров необходимо кликнуть на пост");
  },
};
</script>
<template>
  <div class="container">
    <h1>Micro-Twitter</h1>
    <CreatePost @create="push"></CreatePost>
    <ListOfPosts :posts="posts" @current="newCurrent"></ListOfPosts>
    <ShowPost :current="current" :post="post"></ShowPost>
  </div>
</template>

<style>
.container {
  width: 50vw;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  margin: 0 auto;
}
</style>
