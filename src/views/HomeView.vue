<script>
import NavBar from '@/components/layouts/NavBar.vue'
import BookmarkForm from '@/components/layouts/BookmarkForm.vue'
import bookmarkList from '@/components/layouts/bookmarkList.vue'
import EditBookmark from '@/components/layouts/EditeBookmark.vue'
export default {
  components: {
    NavBar,
    BookmarkForm,
    bookmarkList,
    EditBookmark,
  },
  data() {
    return {
      showForm: false,
      showEditBookmark: false,
      bookmarks: [],
      searchValue: '',
      selectedBookmark: null,
    }
  },
  mounted() {
    const savedBookmarks = JSON.parse(localStorage.getItem('bookmarks'))
    this.bookmarks = savedBookmarks
  },

  methods: {
    addBookmark(object) {
      this.bookmarks.push(object)
      localStorage.setItem('bookmarks', JSON.stringify(this.bookmarks))
      this.$swal.fire({
        title: 'Added!',
        timer: 1500,
        showConfirmButton: false,
        text: 'Your bookmark  added success.',
        icon: 'success',
      })
    },
    deleteBookmark(id) {
      this.$swal
        .fire({
          title: 'Are you sure?',
          text: "You won't be able to revert this!",
          icon: 'warning',
          showCancelButton: true,
          confirmButtonColor: '#155dfc ',
          cancelButtonColor: '#d33',
          confirmButtonText: 'Yes, delete it!',
        })
        .then((result) => {
          if (result.isConfirmed) {
            this.bookmarks = this.bookmarks.filter((b) => b.id !== id)
            localStorage.setItem('bookmarks', JSON.stringify(this.bookmarks))
            this.$swal.fire({
              title: 'Deleted!',
              timer: 1500,
              showConfirmButton: false,
              text: 'Your website link has been deleted.',
              icon: 'success',
            })
          }
        })
    },
    editBookmark(data) {
      const index = this.bookmarks.findIndex((d) => d.id == data.id)
      this.bookmarks.splice(index, 1, data)
      localStorage.setItem('bookmarks', JSON.stringify(this.bookmarks))
      this.$swal.fire({
        title: 'edited!',
        timer: 1500,
        showConfirmButton: false,
        text: 'Your bookmark  edited success.',
        icon: 'success',
      })
    },
    openEdit(event) {
      this.showEditBookmark = event.show
      this.selectedBookmark = event.data
    },
  },
  computed: {
    filteredBookmarks() {
      if (!this.searchValue) return this.bookmarks

      return this.bookmarks.filter((bookmark) =>
        bookmark.title.toLowerCase().includes(this.searchValue.toLowerCase()),
      )
    },
  },
}
</script>
<template>
  <NavBar @showForm="showForm = $event" />

  <div class="max-w-7xl py-4 px-2 md:px-6 mx-auto">
    <div class="flex justify-center flex-col items-center max-w-md mx-auto">
      <label for="search" class="block mb-2.5 text-sm font-medium text-heading sr-only"
        >Search</label
      >
      <div class="relative">
        <div class="absolute inset-y-0 start-0 flex items-center ps-3 pointer-events-none">
          <svg
            class="w-4 h-4 text-body"
            aria-hidden="true"
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            fill="none"
            viewBox="0 0 24 24"
          >
            <path
              stroke="currentColor"
              stroke-linecap="round"
              stroke-width="2"
              d="m21 21-3.5-3.5M17 10a7 7 0 1 1-14 0 7 7 0 0 1 14 0Z"
            />
          </svg>
        </div>

        <input
          type="text"
          id="search"
          v-model="searchValue"
          class="block w-lg p-3 ps-9 bg-transparent border border-gray-400 text-heading text-sm rounded-base shadow-xs placeholder:text-body focus:outline-none rounded-xl"
          placeholder="Search By title..."
        />
      </div>
    </div>
  </div>

  <div
    @click.self="showForm = false"
    :class="showForm == false ? 'hidden' : ''"
    class="absolute inset-0 z-9999 bg-black/50 flex justify-center items-center"
  >
    <transition name="zoom">
      <keep-alive>
        <BookmarkForm v-if="showForm" :addBookmark="addBookmark" @closeModal="showForm = $event" />
      </keep-alive>
    </transition>
  </div>
  <div
    @click.self="showEditBookmark = false"
    :class="showEditBookmark == false ? 'hidden' : ''"
    class="absolute inset-0 z-9999 bg-black/50 flex justify-center items-center"
  >
    <transition name="zoom">
      <EditBookmark
        :bookmark="selectedBookmark"
        @editBookmark="editBookmark($event)"
        v-if="showEditBookmark"
        @closeModal="showEditBookmark = $event"
      />
    </transition>
  </div>

  <div v-if="bookmarks.length > 0">
    <bookmarkList
      @showEditBookmark="openEdit($event)"
      @deleteBookmark="deleteBookmark($event)"
      :bookmarks="filteredBookmarks"
    />
  </div>
  <div v-else class="flex flex-col items-center justify-center py-8">
    <p class="text-lg font-semibold text-indigo-700 mb-1">You do not have any links yet</p>
    <p class="text-sm text-gray-600">
      Click on <span class="font-medium">Add link</span> to add a new link
    </p>
  </div>
</template>

<style>
.zoom-enter-active,
.zoom-leave-active {
  transition: all 0.3s ease;
}

.zoom-enter-from {
  transform: scale(0.7);
  opacity: 0;
}

.zoom-enter-to {
  transform: scale(1);
  opacity: 1;
}
</style>
