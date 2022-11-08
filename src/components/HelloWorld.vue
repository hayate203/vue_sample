<template>
  <div>
    <input v-model="id">
    <p>UserID: {{ id }}</p>
    <input v-model="name">
    <p>UserName: {{ name }}</p>
    <input v-model="mail">
    <p>Email: {{ mail }}</p>
    <button v-on:click="addData">追加する</button>
  </div>
</template>
<script>
import { getDatabase, ref, set } from "firebase/database";

export default {
  name: "DatabaseTest",
  data() {
    return {
      id: "",
      name: "",
      mail: "",
    };
  },
  methods: {
    addData: function () {
      const db = getDatabase();
      set(ref(db, 'users/' + this.id), {
        username: this.name,
        email: this.mail,
      });
      console.log(this.name + this.mail)
      console.log("追加しました。")
    },
  },
};
</script>