<template>
  <div class="home">
    <h1>Home</h1>
    <!-- <PostList :posts="posts" v-if="showPosts" />

    <button @click="showPosts = !showPosts">Toggle Post</button>
    <button @click="posts.pop()">Delete Post</button> -->

    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList :posts="posts" />
    </div>

    <div v-else>Loading ...</div>
  </div>
</template>

<script>
// import { ref } from "vue";
import PostList from "../components/PostList.vue";
import getPosts from "../composables/getPosts";

export default {
  name: "Home",
  components: { PostList },
  setup() {
    // const posts = ref([
    // {
    //   title: "welcome to the blog",
    //   body: "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim. Donec pede justo, fringilla vel, aliquet nec, vulputate eget, arcu. In enim justo, rhoncus ut, imperdiet a, venenatis vitae, justo. Nullam dictum felis eu pede mollis pretium. Integer tincidunt.",
    //   id: 1,
    // },
    // { title: "top 5 css tips", body: "lorem ipsum", id: 2 },
    // ]);
    // const showPosts = ref(true);

    // const posts = ref([])
    // const error = ref(null);

    // const load = async () => {
    //   try {
    //     let data = await fetch("http://localhost:3000/posts");
    //     if (!data.ok) {
    //       throw Error("no data available");
    //     }

    //     posts.value = await data.json();
    //   } catch (err) {
    //     error.value = err.message;
    //     console.log(error.value);
    //   }
    // };
    // load();

    const { posts, error, load } = getPosts();
    load();

    return { posts, error };
  },
};
</script>
