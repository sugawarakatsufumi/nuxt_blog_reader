<template>
  <div>
    <header><Logo /></header>
    <Nuxt />
    <footer>{{categoryList}}フッダーブログリーダー</footer>
  </div>
</template>
<script>
export default {
  async asyncData(context) {
    // 取得先のURL
    const url = "https://www.netamusic.com/wp-json/wp/v2/categories";
    // リクエスト（Get）
    const response = await context.$axios.$get(url);
    console.log(response);
    // 配列で返ってくるのでJSONにして返却
    return {
        categoryList: response
    }
  }
}
</script>
<style>
</style>
