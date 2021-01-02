<template>
  <div id="app" :class="{ 'theme-dark': darkMode }">
    <div class="container">
      <div class="header">
        <i
          class="fas fa-moon"
          v-if="darkMode"
          @click="darkMode = !darkMode"
        ></i>
        <i class="fas fa-sun" v-else @click="darkMode = !darkMode"></i>
      </div>
      <article>
        <img src="https://picsum.photos/536/354" alt="Hello" />
        <p>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Saepe
          numquam, enim officiis tenetur suscipit nesciunt consequuntur
          laboriosam aspernatur recusandae vero minima, quae perferendis
          voluptates voluptas alias, odit est non debitis laborum minus ea neque
          quidem? Magni ipsam ducimus tempore numquam, voluptatum nisi dolorem,
          voluptas reiciendis mollitia veniam animi iste dicta!
        </p>
      </article>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      darkMode: false,
    };
  },
  watch: {
    darkMode: function () {
      localStorage.setItem("darkMode", JSON.stringify(this.darkMode));
    },
  },
  mounted() {
    this.darkMode = JSON.parse(localStorage.getItem("darkMode"));
  },
};
</script>

<style lang="scss">
@import url("https://use.fontawesome.com/releases/v5.8.1/css/all.css");
* {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
* {
  padding: 0px;
  margin: 0px;
  box-sizing: border-box;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  min-width: 90%;
  min-height: 100vh;
  margin: 0px auto;
  transition: all 0.6s ease-in-out;
  background-color: #efefef;
  .container {
    padding: 0.5rem 1rem;
    .header {
      text-align: left;
      i {
        display: inline-block;
        padding: 8px 5px;
        cursor: pointer;
      }
      i.fa-sun {
        color: #9c9a07f3;
      }
      i.fa-moon {
        color: #2c3e50;
      }
    }
    article {
      background-color: white;
      border-radius: 5px;
      box-shadow: 0px 3px 8px rgba($color: #000000, $alpha: 0.1);
      width: fit-content;
      transition: all 0.9s ease-in;
      img {
        width: 100%;
        height: 100%;
        border-radius: 5px 5px 0px 0px;
      }
      p {
        letter-spacing: 0.1rem;
        text-align: justify;
        padding: 10px 15px 25px;
        &::first-letter {
          font-size: 1.9rem;
          line-height: 0.8;
          float: left;
        }
      }
    }
  }
  &.theme-dark {
    background-color: #2b2a2a;
    article {
      background-color: #272f36;
      p {
        color: white;
      }
    }
  }
}
</style>
