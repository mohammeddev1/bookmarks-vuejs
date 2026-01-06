<script>
export default {
  name: 'BookmarkCard',
  props: {
    bookmark: {
      type: Object,
      required: true,
    },
  },
  methods: {},
}
</script>

<template>
  <div
    class="group relative bg-white/40 rounded-xl border border-gray-200 shadow-sm hover:shadow-lg transition-all duration-300 overflow-hidden"
  >
    <!-- Card Content -->
    <div class="p-5">
      <!-- Favicon/Icon Section -->
      <div class="flex items-start gap-4 mb-4">
        <div
          class="shrink-0 w-12 h-12 bg-linear-to-br from-blue-500 to-indigo-600 rounded-lg flex items-center justify-center shadow-md"
        >
          <svg
            class="w-6 h-6 text-white"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M13.828 10.172a4 4 0 00-5.656 0l-4 4a4 4 0 105.656 5.656l1.102-1.101m-.758-4.899a4 4 0 005.656 0l4-4a4 4 0 00-5.656-5.656l-1.1 1.1"
            />
          </svg>
        </div>

        <div class="flex-1 min-w-0">
          <!-- Title -->
          <a :href="bookmark.link" target="_blank">
            <h3
              class="text-lg font-semibold text-heading mb-1 truncate group-hover:text-blue-600 transition-colors"
            >
              {{ bookmark.title }}
            </h3>
          </a>
          <!-- Link -->
          <a
            :href="bookmark.link"
            target="_blank"
            class="text-sm text-blue-500 hover:text-blue-700 truncate block"
            rel="noopener noreferrer"
          >
            {{ bookmark.link }}
          </a>
        </div>
      </div>

      <!-- Action Buttons -->
      <div class="flex items-center justify-end gap-2 pt-3 border-t border-gray-100">
        <button
          @click="$emit('showEditBookmark', { show: true, data: { ...bookmark } })"
          type="button"
          class="flex items-center gap-1.5 px-3 py-1.5 text-sm font-medium text-gray-600 hover:text-blue-600 hover:bg-blue-50 rounded-lg transition-colors"
          title="Edit"
        >
          <svg
            class="w-4 h-4"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z"
            />
          </svg>
          Edit
        </button>
        <button
          type="button"
          @click="$emit('deleteBookmark', bookmark.id)"
          class="flex items-center gap-1.5 px-3 py-1.5 text-sm font-medium text-gray-600 hover:text-red-600 hover:bg-red-50 rounded-lg transition-colors"
          title="Delete"
        >
          <svg
            class="w-4 h-4"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"
            />
          </svg>
          Delete
        </button>
      </div>
    </div>

    <div
      class="absolute top-0 left-0 w-1 h-full bg-linear-to-b from-blue-500 to-indigo-600 opacity-0 group-hover:opacity-100 transition-opacity"
    ></div>
  </div>
</template>

<style scoped>
.line-clamp-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
</style>
