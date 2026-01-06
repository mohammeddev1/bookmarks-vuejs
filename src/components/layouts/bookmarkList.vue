<script>
import BookmarkCard from './BookmarkCard.vue'
export default {
  components: {
    BookmarkCard,
  },
  props: {
    bookmarks: {
      type: Array,
      required: true,
    },
  },
}
</script>

<template>
  <div class="max-w-7xl py-4 px-2 md:px-6 mx-auto">
    <div class="grid grid-cols-1 gap-3 sm:grid-cols-2 md:grid-cols-3 xl:grid-cols-4">
      <template v-for="bookmark in bookmarks" :key="bookmark.id">
        <BookmarkCard
          @showEditBookmark="$emit('showEditBookmark', $event)"
          @deleteBookmark="$emit('deleteBookmark', $event)"
          :bookmark="bookmark"
        />
      </template>
    </div>
  </div>
</template>
