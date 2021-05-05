<template>
  <div id="app">
    <div class="user">
      <img
        class="user__profile"
        alt=""
        src="http://via.placeholder.com/150x150."
      />
      <h2 class="user__name">Taha Ansari</h2>
      <p class="user__email">taha.m.ansari@gmail.com</p>
      <button class="user__getuser">
        Get Random User
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  created() {
    fetch("https://randomuser.me/api")
      .then((response) => response.json())
      .then((data) => console.log(data));
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  font-size: 1rem;
  font-weight: normal;
  box-sizing: border-box;
  font-family: inherit;
}
body {
  line-height: 2;
}
.user {
  padding: 50px;
  background: #ececec;
  text-align: center;
  &__profile {
    width: 150px;
    height: 150px;
    border-radius: 50%;
  }
  &__getuser {
    border: 1px solid;
    padding: 10px;
  }
}
</style>
