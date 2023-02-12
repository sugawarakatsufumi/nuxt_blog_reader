<template>
  <dl style="background-color:#e8e8e8">
    <dt>カテゴリー</dt>
    <dd v-for="category in item.categories">
      <n-link :to="{name:'category-id', params: { id: category } }">
      {{category}}
      </n-link>
    </dd>
  </dl>
</template>
<script>
export default{
  props: ['item'],
}
</script>
<style>
</style>
