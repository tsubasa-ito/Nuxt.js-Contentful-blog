<template>
  <div>
    <Item
         v-for="work in works"
         :key="work.sys.id"
         :work="work"
    />
  </div>
</template>


<script>
import { createClient } from '~/plugins/contentful.js'
import Item from '@/components/Item'

const client = createClient()
export default {
  components: {
    Item
  },
  asyncData() {
  return Promise.all([
    client.getEntries({
      'content_type':'work',
      order: '-sys.createdAt'
  })
    ]).then(([works]) => {
      return {
        works: works.items
    }
    }).catch(console.error)
}
}
</script>
