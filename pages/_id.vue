<template>
  <div class="container">
    <h1>{{posts.title.rendered}}</h1>
    <div class="meta">
        <time>{{posts.modified_gmt}}</time>
        <MetaCategory :item="posts" />
    </div>
    <section v-html="posts.content.rendered"></section>
    
  </div>
</template>

<script>
export default {
  async asyncData(context) {
    const post_id = context.params.id;
    // 取得先のURL
    const url = "https://www.netamusic.com/wp-json/wp/v2/posts/"+post_id;
    // リクエスト（Get）
    const response = await context.$axios.$get(url);
    console.log(response);
    // 配列で返ってくるのでJSONにして返却
    return {
        posts: response
    };
  }
}
</script>