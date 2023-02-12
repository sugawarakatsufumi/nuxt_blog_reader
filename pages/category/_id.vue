<template>
  <div class="container">
    <h1>カテゴリー:{{category_meta.name}} カテID:{{category_id}}</h1>
    <ul id="example-1">
      <li v-for="item in posts" style="border:solid 1px black">
        <MetaCategory :item="item" />
        <n-link :to="{ name: 'id', params: { id: item.id } }">
          {{item.id}}:{{ item.title.rendered }}
        </n-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData(context) {
    const category_id = context.params.id;
    // 取得先のURL
    const category_meta_url = "https://www.netamusic.com//wp-json/wp/v2/categories/"+category_id;
    const posts_url = "https://www.netamusic.com/wp-json/wp/v2/posts?categories="+category_id;
    // リクエスト（Get）
    const category_response = await context.$axios.$get(category_meta_url);
    const posts_response = await context.$axios.$get(posts_url);
    console.log(posts_response);
    // 配列で返ってくるのでJSONにして返却
    return {
        category_meta: category_response,
        posts:  posts_response,
        category_id: category_id,
    };
  }
}
</script>