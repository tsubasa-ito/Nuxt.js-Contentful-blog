<template>
  <div class="w-full m-2 pb-3 bg-white overflow-hidden shadow-lg">
    <nuxt-link :to=" '/category/' + work.fields.category.sys.id ">
      <div class="absolute bg-white py-1 px-3 rounded shadow mt-1 ml-1 text-sm">
        {{ work.fields.category.fields.name }}
      </div>
    </nuxt-link>
    <nuxt-link :to="'/work/' + work.fields.slug">
      <div
        class="mb-3 w-full h-64 bg-center bg-cover"
        :style=" 'background-image: url(' + work.fields.image.fields.file.url + ')' "
      ></div>
        <h3 class="ml-3 font-bold">{{ work.fields.title }}</h3>
      <h4 class="ml-3 my-2 text-xs">{{ work.fields.subtitle }}</h4>
    </nuxt-link>
    <div class="flex ml-2">
      <li
        v-for="tag in work.fields.tag"
        :key="tag.sys.id"
        @click="$router.push('/tag/'+tag.sys.id)"
        class="list-none text-xs m-1 bg-gray-200 p-1 rounded cursor-pointer"
      >
        {{ tag.fields.name }}
      </li>
    </div>
  </div>
</template>

<script>
export default {
  props: ['work']
}
</script>

<style>

</style>
