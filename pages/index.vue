<template>
  <div class="container">
    <h1>目次</h1>
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
    // 取得先のURL
    const url = "https://www.netamusic.com/wp-json/wp/v2/posts?&_embed";
    // リクエスト（Get）
    const response = await this.$axios.$get(url);
    //console.log(response);
    // 配列で返ってくるのでJSONにして返却
    return {
        posts: response
    };
  }
}
</script>