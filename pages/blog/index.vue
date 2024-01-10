<template>
  <main>
    <section v-if="posts" class="w-full max-w-5xl mx-auto">
      <h1 class="title">ပွဲကြို သုံးသပ်ချက်များ</h1>
      <posts post-type="blog" :amount="10" />
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let posts;
    try {
      posts = await $content("blog").fetch();
    } catch (e) {
      error({ message: "သုံးသပ်ချက်များ ရှာမတွေ့ပါ" });
    }
    return { posts };
  },
}
</script>
