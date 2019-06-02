<template>
  <div class="admin-new-post-page">
    <section class="new-post-form">
      <AdminPostForm @submit="onSubmitted" />
    </section>
  </div>
</template>

<script>
import axios from "axios";
import AdminPostForm from "@/components/Admin/AdminPostForm";

export default {
  layout: 'admin',
  methods: {
    onSubmitted(postData) {
      axios.post('https://nuxt-blog-21525.firebaseio.com/posts.json', postData)
      .then(result => console.log(result))
      .catch(e => console.log(e))
    }
  },
  components: {
    AdminPostForm
  }
};
</script>

<style scoped>
.new-post-form {
  width: 90%;
  margin: 20px auto;
}

@media (min-width: 768px) {
  .new-post-form {
    width: 500px;
  }
}
</style>

