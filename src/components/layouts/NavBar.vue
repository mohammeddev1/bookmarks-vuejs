<script>
import Logo from '../../../public/logo.svg'
import BaseButton from '../ui/BaseButton.vue'
export default {
  props: {
    showForm: {
      type: Boolean,
    },
  },
  components: {
    BaseButton,
  },
  data() {
    return {
      title: 'Linkaty',
      Logo,
    }
  },
}
</script>
<template>
  <nav class="shadow rounded-b-2xl">
    <div class="max-w-7xl py-4 px-2 md:px-6 mx-auto">
      <div class="flex items-center justify-between">
        <!-- Logo -->
        <div class="flex items-center gap-1">
          <img :src="Logo" alt="logo" class="w-10 h-10" />
          <h1 class="text-indigo-900 font-noto text-2xl md:text-3xl">{{ title }}</h1>
        </div>
        <!-- button Add bookmark -->
        <BaseButton
          @click="$emit('showForm', true)"
          class="text-white bg-blue-600 hover:bg-blue-700 shadow-xs rounded-2xl cursor-pointer focus:outline-none"
        >
          <template #buttonText> add Link </template>
        </BaseButton>
      </div>
    </div>
  </nav>
</template>
