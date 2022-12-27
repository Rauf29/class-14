<template>
  <button @click="addPost">
    Add Post
  </button>
  <br>
<!--  fev count:{{fevCount}} <br>-->
<!--  Un fev count: {{unFevCount}}-->
  <h2>All Posts</h2>
  <ul>
  <single-post
      style="margin-bottom: 10px"
      v-for="(post, index) in posts"
      key="index"
      :post = "post"
      @delete = "Click"
      @fev="handleFev"
  />
  </ul>
  <br>
  <h2>Fevs</h2>
  <ul>
    <single-post
        style="margin-bottom: 10px"
        v-for="(post, index) in fevs"
        key="index"
        :post = "post"
        @delete = "Click"
        @fev="handleFev"
    />
  </ul>
  <br>
  <h2>UnFevs</h2>
  <br>
  <ul>
    <single-post
        style="margin-bottom: 10px"
        v-for="(post, index) in unFevs"
        key="index"
        :post = "post"
        @delete = "Click"
        @fev="handleFev"
    />
  </ul>
<h1>{{ message }}</h1>
  <ul>
 <Number/>
  </ul>
  <SchoolName/>
  <slot-component>
    My name is Rauf
  </slot-component>
</template>

<script>
import Number from "@/components/Number.vue";
import SchoolName from "@/components/SchoolName.vue";
import SlotComponent from "@/components/SlotComponent.vue";
import SinglePost from "@/components/SinglePost.vue";

export default {
  name: "HomePage",
  components: {SinglePost
    ,SlotComponent, SchoolName, Number
  },
  data() {
    return {
      message: "Hello Bangladesh",
      posts: [
        {
          id: 1,
          title:"Post 1",
          fev: true
        },
        {
          id: 2,
          title:"Post 2",
          fev: false
        },
        {
          id: 3,
          title:"Post 3",
          fev: true
        }
      ],
      first_name: "Rauf",
      last_name: "Islam"
    }
  },
  computed: {
    fevs() {
      return this.posts.filter(post=> post.fev)
    },
    unFevs() {
      return this.posts.filter(post => !post.fev)
    }
  },
  methods: {
    Click(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    },
    addPost() {
      this.posts.push({
        id: this.posts.length +1,
        title: `post ${this.posts.length +1}`
      })
    },
    handleFev(post) {
    this.posts = this.posts.map(p=> {
      if (p.id === post.id) {
        p.fev = !p.fev
      }
      return p
    })
    }
  }

}
</script>

<style scoped>

h1 {
  color: green;
}
</style>

// beforeCreate() {
//   console.log('HomePage beforeCreate');
// },
// created() {
//   console.log('HomePage Created');
// },
// beforeMount() {
//   console.log('HomePage beforeMount');
// },
// mounted() {
//   console.log('HomePage mounted');
// },
// beforeUnmount() {
//   console.log('HomePage beforeUnmount');
// },
// unmounted() {
//   console.log('Homepage unmounted');
// },