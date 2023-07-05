<script>
/* Создать редактор постов на вью,который состоит из 4 компонентов: главный, компонент создания поста,компонент список постов и компонент для отображения каждого отдельного поста в списке,использовать все полученные знания: директивы,обмен данными между компонентами, стилизация компонентов.Дополнительно: реализовать оформление каждого поста в виде: выбора цвета фона,цвета шрифта, размера шрифта.
 */

export default {
  data() {
    return {
      post: {
        title: "",
        body: "",
        fontSize: 14,
        color: "white",
        fontFamily: "Sans-Serif",
      },
    };
  },
  methods: {
    sendPost() {
      if (this.post.title.trim() !== "" && this.post.body.trim() !== "") {
        this.post.id = Date.now();
        const date = new Date();

        const hours = date.getHours().toString().padStart(2, "0");
        const minutes = date.getMinutes().toString().padStart(2, "0");

        const day = date.getDate();
        const month = date.toLocaleString("default", { month: "short" });

        const formattedTime = `${hours}:${minutes} (${day} ${month})`;
        this.post.time = formattedTime;
        this.$emit("create", this.post);

        this.post.title = "";
        this.post.body = "";
      } else {
        alert("Заполните поля");
      }
    },
  },
};
</script>
<template>
  <div class="create-container">
    <input v-model="post.title" type="text" placeholder="Title" />
    <input v-model="post.body" type="text" placeholder="Text" />
    <button @click="sendPost">Add</button>
  </div>
</template>

<style>
.create-container {
  display: flex;
  justify-content: space-between;
  width: 50vw;
  margin: 0 auto;
  border: 2px solid rgb(0, 19, 192);
  border-radius: 15px;
  padding: 5vh 2.5vw;
}
.create-container * {
  padding: 1vh 1vw;
  border-radius: 10px;
  transition: 0.2s ease-in-out;
}
.create-container *:hover {
  border-radius: 15px;
}
.create-container input {
  width: 30%;
  outline: none;
}

.create-container button {
  width: 20%;
  cursor: pointer;
}
</style>
