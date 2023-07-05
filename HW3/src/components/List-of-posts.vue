<script>
/* Создать редактор постов на вью,который состоит из 4 компонентов: главный, компонент создания поста,компонент список постов и компонент для отображения каждого отдельного поста в списке,использовать все полученные знания: директивы,обмен данными между компонентами, стилизация компонентов.Дополнительно: реализовать оформление каждого поста в виде: выбора цвета фона,цвета шрифта, размера шрифта.
 */

export default {
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {};
  },
  methods: {
    sendCurrent(id) {
      this.posts.forEach((post) => {
        if (post.id == id) {
          this.$emit("current", post);
        }
      });
    },
  },
  mounted() {
    setInterval(() => {
      console.log(this.posts);
    }, 5000);
  },
};
</script>
<template>
  <div class="container-posts">
    <div
      v-for="post in posts"
      class="post-item"
      @click="sendCurrent(post.id)"
      :style="{
        color: post.color,
        fontFamily: post.fontFamily,
        fontSize: post.fontSize + 'px',
      }"
    >
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>
  </div>
</template>

<style>
.container-posts {
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 50vw;
  align-items: center;
  padding: 10px;
}
.post-item {
  text-align: center;
  width: 30vw;
  border: 1px solid white;
  border-radius: 10px;
  cursor: pointer;

}
</style>
