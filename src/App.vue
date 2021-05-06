<template>
  <div id="app">
    <div class="user" :class="users.gender">
      <img class="user__profile" alt="" :src="users.picture.large" />
      <div>
        {{ users.name.title + " " + users.name.first + " " + users.name.last }}
      </div>
      <div>
        {{ users.email }}
      </div>
      <button @click="getRandomUser" class="user__getuser">
        Get Random User
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      users: [],
    };
  },
  async created() {
    console.log("created hook called");

    // this.getRandomUser();
    // async getRandomUser() {
    const res = await fetch("https://randomuser.me/api");
    const { results } = await res.json();
    this.users = results[0];
    // },
  },
  methods: {
    // getRandomUser() {
    //   fetch("https://randomuser.me/api")
    //     .then((res) => {
    //       if (res.ok) {
    //         console.log("SUCCESS");
    //         return res.json();
    //       } else {
    //         console.log("FAILED");
    //       }
    //     })
    //     .then((data) => (this.users = data.results[0]))
    //     .catch((err) => console.log("My Error: ", err));
    // },
    async getRandomUser() {
      console.log("this function is asyncronously called");
      const res = await fetch("https://randomuser.me/api");
      const { results } = await res.json();
      this.users = results[0];
    },
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto&display=swap");

* {
  margin: 0;
  padding: 0;
  font-size: 1rem;
  font-weight: normal;
  box-sizing: border-box;
  font-family: inherit;
}

body {
  font-family: "Roboto", sans-serif;
  line-height: 1.8;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  margin: 0.4em 0;
}

p {
  margin: 10px 0;
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
    padding: 10px 20px;
    cursor: pointer;
    margin-top: 15px;
    font-size: 14px;
    background: transparent;
    border: none;
    border-radius: 25px;
  }
  &.male {
    .user__getuser {
      border: 1px solid #585858;
      color: #585858;
      &:hover {
        background: #585858;
        color: #ececec;
      }
    }
    .user__profile {
      border: 4px solid #585858;
    }
  }
  &.female {
    .user__getuser {
      border: 1px solid pink;
      color: pink;
      &:hover {
        background: pink;
        color: #ffffff;
      }
    }
    .user__profile {
      border: 4px solid pink;
    }
  }
}
</style>
