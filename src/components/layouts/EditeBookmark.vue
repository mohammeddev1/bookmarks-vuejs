<template>
  <div class="max-w-lg p-6 rounded-3xl w-full bg-indigo-200">
    <form @submit.prevent class="space-y-4 relative flex flex-col justify-center">
      <button
        @click="closForm()"
        class="absolute -top-2.5 w-6 flex text-lg p-1.5 cursor-pointer justify-center items-center rounded-4xl h-6 transition-colors duration-150 hover:bg-indigo-100 right-1"
      >
        X
      </button>
      <div>
        <label for="title" class="block mb-1 ml-1.5 text-sm font-medium text-heading">
          Website Title</label
        >
        <input
          type="text"
          id="title"
          v-model="formData.title"
          class="border focus:outline-none rounded-lg border-gray-500 text-heading text-sm rounded-base block w-full px-3 py-2.5 shadow-xs placeholder:text-body"
          placeholder="title..."
        />
        <p ref="titleError" class="text-sm font-semibold text-red-600 mt-1"></p>
      </div>
      <div>
        <label for="link" class="block mb-1 ml-1.5 text-sm font-medium text-heading">
          Website Link</label
        >
        <input
          type="text"
          id="link"
          v-model="formData.link"
          class="border rounded-lg focus:outline-none border-gray-500 text-heading text-sm rounded-base block w-full px-3 py-2.5 shadow-xs placeholder:text-body"
          placeholder="link..."
        />
        <p ref="linkError" class="text-sm font-semibold text-red-600 mt-1"></p>
      </div>

      <button
        type="button"
        @click="edit()"
        class="text-white w-60 mx-auto bg-green-600 hover:bg-green-800 cursor-pointer box-border border border-transparent shadow-xs font-medium leading-5 rounded-lg text-xs px-3 py-1.5 focus:outline-none"
      >
        edit website
      </button>
    </form>
  </div>
</template>

<script>
export default {
  props: {
    bookmark: {
      type: Object,
    },
  },
  data() {
    return {
      formData: this.bookmark,
    }
  },
  methods: {
    closForm() {
      this.$emit('closeModal', false)
    },

    edit() {
      let isValid = true
      const title = this.formData.title.trim()
      const link = this.formData.link.trim()

      const linkPattern =
        /^(https?:\/\/)?(www\.)?([a-z0-9][-a-z0-9]{0,62}\.)+[a-z]{2,24}(\/[^\s]*)?$/i

      if (this.$refs.titleError) this.$refs.titleError.innerText = ''
      if (this.$refs.linkError) this.$refs.linkError.innerText = ''

      if (!title) {
        if (this.$refs.titleError)
          this.$refs.titleError.innerText = 'title is required, please add title'
        isValid = false
      }

      if (!link) {
        if (this.$refs.linkError)
          this.$refs.linkError.innerText = 'link is required, please add link'
        isValid = false
      } else if (!linkPattern.test(link)) {
        if (this.$refs.linkError)
          this.$refs.linkError.innerText = 'link not correct, please add correct link'
        isValid = false
      }

      if (!isValid) return
      this.$emit('editBookmark', { ...this.formData })
      this.closForm()
      this.formData.title = ''
      this.formData.link = ''
    },
  },
}
</script>
