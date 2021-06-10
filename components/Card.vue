<template>
  <div
    :class="stated ? 'bg-green-200' : 'bg-blue-100'"
    class="rounded-md container h-500 p-1 flex justify-between my-2"
  >
    <div class="p-5 border-l-4 border-blue-500 text-blue-500 text-sm font-bold">
      {{ title }}
    </div>
    <div class="actions flex items-center">
      <button
        :class="!stated ? 'bg-green-400' : 'bg-red-400'"
        class="text-white rounded-full px-3 h-8 mx-1 focus:outline-none"
        @click="$emit('update')"
      >
        {{ !stated ? "&#10003;" : "&#215;" }}
      </button>
      <button
        class="
          bg-red-500
          rounded-full
          text-white
          px-3
          h-8
          mx-1
          focus:outline-none
        "
        @click="$emit('delete')"
      >
        &#215;
      </button>
    </div>
  </div>
</template>


<script>
export default {
  name: "Card",
  props: {
    title: { type: String, default: "" },
    stated: { type: Boolean, default: false },
  },
};
</script>