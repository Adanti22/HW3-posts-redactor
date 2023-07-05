<script>
/* Создать редактор постов на вью,который состоит из 4 компонентов: главный, компонент создания поста,компонент список постов и компонент для отображения каждого отдельного поста в списке,использовать все полученные знания: директивы,обмен данными между компонентами, стилизация компонентов.Дополнительно: реализовать оформление каждого поста в виде: выбора цвета фона,цвета шрифта, размера шрифта.
 */

export default {
  props: ["post", "current"],
  data() {
    return {
      ff: "",
      fz: "",
      cr: "",
    };
  },
  methods: {
    show() {
      console.log(this.post);
    },
    changeParams() {
      this.post.fontFamily = this.ff;
      this.post.color = this.cr;
      this.post.fontSize = this.fz;
      console.log(this.post);
    },
  },
};
</script>
<template>
  <div
    class="show-container show"
    :class="{ visible: current, hidden: !current }"
    @click="show"
  >
    <h1>Current post</h1>
    <div class="post" v-for="(value, key) in post" :key="key">
      <h3 v-if="key === 'title'">Title: {{ value }}</h3>
      <p v-if="key === 'body'">Body: {{ value }}</p>
      <p v-if="key === 'time'">{{ value }}</p>
    </div>
  </div>
  <div
    class="show-container edit"
    :class="{ visible: current, hidden: !current }"
  >
    <div class="params" v-for="(value, key) in post" :key="key">
      <select v-if="key === 'fontSize'" :value="value" v-model="fz">
        <option value="14">14px</option>
        <option value="16">16px</option>
        <option value="18">18px</option>
        <option value="20">20px</option>
      </select>
      <select v-if="key === 'fontFamily'" :value="value" v-model="ff">
        <option value="Georgia">Georgia</option>
        <option value="Arial">Arial</option>
        <option value="Times New Roman">Times New Roman</option>
      </select>
      <select v-if="key === 'color'" :value="value" v-model="cr">
        <option value="white">White</option>
        <option value="gray">Gray</option>
        <option value="red">Red</option>
        <option value="blue">Blue</option>
      </select>
    </div>
    <button class="edit-btn" @click="changeParams">Edit</button>
  </div>
</template>

<style>
.show-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 1px solid rgb(195, 195, 195);
  position: absolute;
  padding: 10px;
}
.show {
  left: 3vw;
}
.edit-btn {
  cursor: pointer;
  background-color: aquamarine;
  padding: 5px 10px;
  border-radius: 10px;
  margin-top: 10px;
}
.edit {
  left: 3vw;
  top: 50vh;
}
h1 {
  margin-bottom: 10px;
}

.hidden {
  display: none;
}
.visible {
  display: block;
}
.post {
  text-align: center;
}
</style>
